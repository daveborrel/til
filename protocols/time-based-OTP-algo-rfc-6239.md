# TOTP: Time-Based One-Time Password Algorithm

This is an extension of the HMAC-based OTP algorithm, but now it supports a time-based moving factor.

The output of HMAC-SHA-1 is this:

```
HOTP(K,C) = Truncate(HMAC-SHA-1(K,C))
```

TOTP = HOTP(K, T)

K = "secret"
C = Current Unix Time - T0 / X

Hashing algorithm will be - HMAC-SHA-512

Current Unix Time - the number of seconds elapsed since midnight UTC of January 1, 1970
