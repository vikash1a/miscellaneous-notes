JWT (Json Web Token) is used for implementing authentication 
and authorisation.

## JWT
- Header - Type of token and signing algorithm
- Payload - Claims about an entity and additional data
- Signature - Ensures the integrity of token and verifies its authenticity
  - It is the signed hash of header and payload. So if header or payload is modified by user it will  become invalid.
  - ```
    HMACSHA256(
        base64UrlEncode(header) + "." + base64UrlEncode(payload),
        secret_key
    )
    ```

Structure - `<header>.<payload>.<signature>`

### Example 
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjEyMywicm9sZSI6ImFkbWluIiwiZXhwIjoxNjcwMjUwMDAwfQ.sKjH5IlNiUpNcGbbOFHAbHQ1RQ-XZxRtX1CdT8PR-YA
```
#### Header
- `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9`
- base64 decoded as,
```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

#### Payload
- `eyJ1c2VySWQiOjEyMywicm9sZSI6ImFkbWluIiwiZXhwIjoxNjcwMjUwMDAwfQ`
- base64 decoded as,
```json
{
  "userId": 123,
  "role": "admin",
  "exp": 1670250000
}
```

#### Signature
- `sKjH5IlNiUpNcGbbOFHAbHQ1RQ-XZxRtX1CdT8PR-YA`
- base64 decoded as,
```
HMACSHA256(
    base64UrlEncode(header) + "." + base64UrlEncode(payload),
    secret_key
)
```

## Cryptography for JWT
### Symmetric Cryptographic (HMAC)
- Only secret/private key is used

### Asymmetric Cryptographic (RSA/ECDSA)
- private key for signing and public key for verification 

## Notes
- Header and payload is not encoded by default, if they are it called as JWE (Json web Encryption Token)
- The size of the text(digest) after hashing is always same for the given hash function
  - SHA-256 - 256 bit (32 byte)
  - SHA-1 - 160 bit (20 byte)
  - MD5 128-bit (16 byte)