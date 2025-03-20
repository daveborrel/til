# JSON Web Token (JWT)

JWT securely transmits messages between two parties as a JSON object. Composed of a header, payload, and signature.

Mainly used for **Authorization** - Once a user is logged in, then each request will have a JWT to ensure that it is the same user.

It will look like this:

```
xxxxx.yyyyy.zzzzz
```

**What it is composed of:**

- header - determines which signing algorithm to use
- payload - information about user
- signature - ensures token was not changed

**How does it work?**

1. After a user successfully logs in, the server creates and signs a JWT for user with a secret
2. When a user wants to access resources they sent a request with the HWT in the header `Authorization: Bearer <token>`
3. Server checks for this valid JWT, and then returns the resources.

**Main advantage over session ID stored in cookie**

- Does not need to be stored in the server's memory.
- Helps avoid situations where servers have different session numbers.
- Allows users to use the same JWT to different servers as long as they have the same secret key.

### Sources

[rfc](https://datatracker.ietf.org/doc/html/rfc7519)
[jwt.io](https://jwt.io/introduction)
