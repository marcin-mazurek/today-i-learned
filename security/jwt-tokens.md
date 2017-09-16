# JWT tokens
JWT = JSON web token

It's a standard of passing user related information in a secure and compact way between parties.
The most common use case is authentication and authorization, where parties are a web application and an authorization service. 

## Token structure
A token looks like this (new lines are just inserted for visibility):
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.
eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWV9.
TJVA95OrM7E2cBab30RMHrHDcEfxjoYZgeFONFh7HgQ
```
There are three parts separated by a dot sign: header, payload and signature.

### Header
Encoded with base64, contains two information:
* type of the token (as you can expect - JWT)
* hashing algorithm used (eg. HMAC SHA256, RSA) for signature

### Payload
The body of the token, contains any information you may need (like ACLs), serialized to a JSON object and encoded with base64.
There are a few _reserved claims_, basically a JSON keys that are recommended to declare by the standard. Some of them are:

* iss - issuer
* exp - expiration time
* sub - subject
* aud - audience

### Signature
Makes sure that we can trust the token and it wasn't created by an attacker.

It's a combination of the encoded header and the encoded payload concatenated with the header using a dot sign,
hashed by a secret key known only to the applications transfering the data.

## Advantages
* lightweight - can be stored in a cookie,
* self-contained - contains all information about the user, there's no need to query database on each request

## Where to store JWT tokens
In secure cookies (using HTTPS, flagged as Secure).
LocalStorage/SessionStorage is not a secure place and is vurnerable to XSS attacks.
