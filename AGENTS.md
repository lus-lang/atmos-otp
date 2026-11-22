# AGENTS.md

`lus-lang/atmos-otp` is the repository of the `otp` package of the atmosphere registry. Programs load the package with `require("https://atmosp.here/2.0/otp.lus")`.

## Scope

`otp` generates and checks one-time passwords for two-factor sign in: HOTP from RFC 4226 and TOTP from RFC 6238, with base32 secrets and `otpauth://` URIs for authenticator apps. The public API is every function that `otp.lus` returns in its module table. A change to that API needs a new entry in `CHANGELOG.md` and a version change in the header.

## Layout

- `otp.lus` is the whole package. Its header doc comment contains the package metadata and the declared permissions.
- `tests/*_test.lus` are the tests. They load `otp.lus` from the parent of `TEST_DIR`, the directory that holds the test file.

## Commands

Run these commands from the root of the repository.

```sh
lus test tests          # run the tests
lus check otp.lus     # lint, including the package codes
lus doc otp.lus       # print the reference
```

## Rules

- Every public function has a doc comment that states each result and each error, following `spec/design/style.md` of the Lus repository.
- The package never calls `pledge`. A new permission is declared in the header and in the README.
- Prose follows the `lus-writing` skill, which `lus agents init` installs and https://lus.dev/agents/skills/lus-writing/SKILL.md serves. In particular, prose has no dashes or semicolons and never names the Roblox Lua dialect.
- Every bug fix comes with a test that fails without it.
