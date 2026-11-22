# otp

Generates and checks one-time passwords for two-factor sign in: HOTP from RFC 4226 and TOTP from RFC 6238, with base32 secrets and `otpauth://` URIs for authenticator apps.

```lus nocheck
local otp = require("https://atmosp.here/2.0/otp.lus")

local secret = otp.secret()
print(otp.uri(secret, { issuer = "App", account = "ada@example.com" }))

-- Keep the last accepted step, so that a code works only once.
local offset, step = otp.verify(secret, "492039", { window = 1 })
if offset and step > last_step then
    last_step = step
end
```

The package requires Lus 2.0. It needs no permissions. It calls no `pledge` of its own, so the program that loads it keeps control of its permissions.

The reference is in the doc comments of `otp.lus`. Run `lus doc otp.lus` to print it.
