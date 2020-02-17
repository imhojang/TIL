# JWT. JSON Web Token Explained

---

## What is JSON Web Token?

- Open standard (anyone can use it)
- Why use it? Securely transfer information between any two bodies
- Digitally Signed - information is verified and trusted
- Compact
  - JWT can be send via URL, POST request, HTTP Header
  - Fast Transmission
- Self Contained
  - contains information about the user
  - Avoiding query the database more than once.

## JWT is useful

- authentication
- information exchange

## What is the Web Token structure?

aaaaaaaa.bbbbbbbb.cccccccc

- Header ('a' part)

```JSON
{
  "alg": "HS256"
  "typ": "JWT"
}
```

- alg: algorithm like HMAC SHA256 or RSA
- typ: type of JWT token
- This JSON is Base64Url encoded to form its part

- Payload

  - it contains claims: user details or additional metadata
  - payload is then Base64Url encoded to form the second part

- Signature

  ```JSON
  HMACSHA256(
    base64UrlEncode(header) + "." +
    base64UrlEncode(payload),
    secret
  )
  ```

  - Combine base64 header and base64 payload with secret.
  - Provides more security

### Combine all three to from JWT!

- combine with dot (.)



## How do JSON web tokens work?

Brower & Server

1. Post request to login with Credentials
2. Generate JWT via Seceret
3. Return the JWT to the client (browser)
4. Send the JWT on the Authorization header
5. Check JWT signature and get user info
6. Send response to the client (browser)

---

# Node.js API Authentication with JWT

## 