# Asynchronous python library for Steam authorization using protobuf

[![pypi: package](https://img.shields.io/badge/pypi-1.1.2-blue)](https://pypi.org/project/pysteamauth/)
[![Python: versions](
https://img.shields.io/badge/python-3.9%20%7C%203.10%20%7C%203.11%20%7C%203.12-blue)]()


## Install

```bash
pip install pysteamauth
```


## Usage

```python
from pysteamauth.auth import Steam


async def main():
    steam = Steam(
        login='login', 
        password='password',
    )
    
    await steam.login_to_steam()

    await steam.request('https://steamcommunity.com')
    await steam.request('https://store.steampowered.com')
    await steam.request('https://help.steampowered.com')
```

## If account have Steam Guard

```python
from pysteamauth.auth import Steam

steam = Steam(
    login='login',
    password='password',
    shared_secret='shared_secret',
)
```

## Cookie storage

Library uses default cookie storage `BaseCookieStorage`, which stores Steam cookies in application memory.
But you can write own cookie storage. For example, redis storage:

```python
import json
from typing import Dict

from aioredis import Redis
from pysteamauth.abstract import CookieStorageAbstract
from pysteamauth.auth import Steam


class RedisStorage(CookieStorageAbstract):

    redis = Redis()

    async def set(self, login: str, cookies: Dict) -> None:
        await self.redis.set(login, json.dumps(cookies))

    async def get(self, login: str, domain: str) -> Dict:
        cookies = await self.redis.get(login)
        if not cookies:
            return {}
        return json.loads(cookies).get(domain, {})


async def main():
    steam = Steam(
        login='login',
        password='password',
        cookie_storage=RedisStorage(),
    )
    
    await steam.login_to_steam()
```

## Error processing

```python
from pysteamauth.auth import Steam
from pysteamauth.errors import SteamError


async def main():
    try:
        await Steam('login', 'password').login_to_steam()
    except SteamError as error:
        print(error)
```

#### Or

```python
from pysteamauth.auth import Steam
from pysteamauth.errors import SteamError, custom_error_exception


class LoginError(SteamError):
    ...


class RateLimitExceeded(SteamError):
    ...


custom_error_exception({
    5: LoginError,
    84: RateLimitExceeded,
})


async def main():
    try:
        await Steam('login', 'password').login_to_steam()
    except LoginError as error:
        print(error)
```

#### Output
`{'error': 'InvalidPassword', 'code': 5}`

## Proto files

- https://github.com/SteamDatabase/Protobufs/blob/master/steam/enums.proto
- https://github.com/SteamDatabase/Protobufs/blob/master/steam/steammessages_base.proto
- https://github.com/SteamDatabase/Protobufs/blob/master/steam/steammessages_auth.steamclient.proto
- https://github.com/SteamDatabase/Protobufs/blob/master/steam/steammessages_unified_base.steamclient.proto

## License

MIT