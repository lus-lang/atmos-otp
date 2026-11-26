# Changelog

## 1.0.0

**Release date:** TBD

Version 1.0.0 is the first release of `otp`, which runs on Lus 2.0.

- Added the `otp` package.
  - `otp.hotp`: Returns the HOTP code of a counter.
  - `otp.totp`: Returns the TOTP code of a point in time.
  - `otp.verify`: Checks a TOTP code and returns the time step that it matches.
  - `otp.verify_hotp`: Checks an HOTP code and returns the counter that it matches.
  - `otp.remaining`: Returns the seconds left before the current TOTP code changes.
  - `otp.secret`: Returns a new random secret as base32 text.
  - `otp.uri`: Builds the `otpauth://` URI that authenticator apps read from a QR code.
  - `otp.base32_encode`: Encodes bytes in the base32 alphabet of RFC 4648.
  - `otp.base32_decode`: Decodes base32 text into bytes.
  - `otp.iserror`: Returns true for an error object that `otp` raised.
