# Changelog

## [v1.1.0 (2024-20-20)](https://github.com/sometastycake/pysteamauth/releases/tag/v1.1.0)

- Removed support python 3.7 and python 3.8
- Use strict versions of dependencies
- Bump versions of dependencies

## [v1.0.0 (2023-01-22)](https://github.com/sometastycake/pysteamauth/releases/tag/v1.0.0)

- `get_steam_guard` method is classmethod now
- Removed docstrings
- Added new properties to Steam class
- Removed `AuthenticatorData` schema
- Removed `SteamAuthorizationStatus` schema
- Removed `ServerTimeResponse` schema
- Removed `get_host_from_url` function
- Initialize `steamid` if it doesn't specify
- Steam class now accepts objects of `BaseRequestStrategy` and `BaseCookieStorage`

## [v0.0.8 (2022-11-15)](https://github.com/sometastycake/pysteamauth/releases/tag/v0.0.8)

- Removed default value for `domain` parameter in cookie storage

## [v0.0.7 (2022-10-02)](https://github.com/sometastycake/pysteamauth/releases/tag/v0.0.7)

- Removed useless exceptions

## [v0.0.6 (2022-09-28)](https://github.com/sometastycake/pysteamauth/releases/tag/v0.0.6)

- Fixed `check_http_status` method

## [v0.0.5 (2022-09-25)](https://github.com/sometastycake/pysteamauth/releases/tag/v0.0.5)

- Updated protobuf version

## [v0.0.4 (2022-09-25)](https://github.com/sometastycake/pysteamauth/releases/tag/v0.0.4)

- Reduced versions of dependencies

## [v0.0.3 (2022-09-25)](https://github.com/sometastycake/pysteamauth/releases/tag/v0.0.3)

- Using another method for Steam authorization requests which receive bytes

## [v0.0.2 (2022-09-24)](https://github.com/sometastycake/pysteamauth/releases/tag/v0.0.2)

- New method of calculating confirmation hash
- Ability to define custom exceptions for various http status codes from Steam
- Removed method of cookie cleaning from cookie storage
- Method for checking errors from Steam
- New exceptions for Steam errors
- Steam class has beginned receive new parameters
- New method to get Steam sessionid
- Methods to get steamid and authenticator data

## [v0.0.1 (2022-09-14)](https://github.com/sometastycake/pysteamauth/releases/tag/v0.0.1)

- Steam authorization using protobuf
- Steam error handling
- Requests with Steam session
- Ability to define custom exceptions
