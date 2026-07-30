Can be read by everyone, can't modify without secret.
Starts with `ey
Parse: https://jwt.io/
## Format
Has multiple dot separated sections.
base64url = base64, but replace `+` by `-`, replace `/` by `_` and doesn't require padding.
### Header
Is a base64url encoded JSON.
Usually of the following format:
```json
{
	"alg": "algorithm_name",
	"typ": "JWT"
}
```
### Payload
Is a base64url encoded json.
Can include anything you want.
There are 7 Registered Claims which means standard fields that are commonly included:
- `iat` - issued at time, creation time as timestamp
- `jti` - unique ID, prevent JWT reuse.
- `iss` - issuer of JWT
- `sub` - subject of JWT
- `aud` - audience of JWT, intended recipient
- `exp` - expiration time, as timestamp
- `nbf` - not before time, time before which the JWT mustn't be accepted, as timestamp
### Signature
Validates the integrity of the token, prevents modifications.
Is according to the algorithm used.
Is the signature of the `{header}.{payload}`
## Algorithms
### HS256
Uses `HMAC-SHA256` hash.
Has only secret key, symmetric.
Secret key is used both to verify and sign.
### RS256
Uses `RSASHA256` hash.
Has public and private key, asymmetric.
Private key is used to generate the signature and the public key to validate.
### none
No signature.
## Tricks
- set algorithm to `none`, it disables the signature and if the server doesn't check it will allow modifications. https://www.gavinjl.me/edit-jwt-online-alg-none/