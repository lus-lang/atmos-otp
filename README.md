# otp

`otp` generates and checks one-time passwords for two-factor sign in: HOTP from RFC 4226 and TOTP from RFC 6238, with base32 secrets and `otpauth://` URIs for authenticator apps.

The following example enrolls a forum account in two-factor sign in, then accepts each code that the user types only once.

```lus nocheck
local otp = require("https://atmosp.here/2.0/otp.lus")

local secret = otp.secret()
print(otp.uri(secret, { issuer = "Lus Forum", account = "ada@example.com" }))

-- Keep the last accepted step, so that a code works only once.
local offset, step = otp.verify(secret, "492039", { window = 1 })
if offset and step > last_step then
    last_step = step
end
```

The package requires Lus 2.0 and declares no permissions. It never calls `pledge`, so the program that loads it keeps control of its permissions.

The reference is in the doc comments of `otp.lus`, which `lus doc otp.lus` prints.
