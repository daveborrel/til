# RFC2617 - HTTP Authentication: Basic and Digest Access Authentication

This document goes over the basic authentication scheme for http requests.

1. Server sends `WWW-Authenticate: Basic realm="WallyWorld"`
2. Client will send `Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==` as a response

- Given a username: Alladin and password : open sesame
- Put it into this format username:password
- Convert that into base64

### RFC6238 TOTP

### Sources

[RFC-2617](https://datatracker.ietf.org/doc/html/rfc2617#section-2)
