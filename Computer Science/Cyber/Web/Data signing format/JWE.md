Similar to JWT but also encrypts.
can be encrypted/decrypted using https://www.authgear.com/tools/jwt-jwe-debugger
Has 5 parts and the header looks like this:
```json
{
	"cty": "JWT",
	"enc": "A256GCM",
	"alg": "RSA-OAEP-256"
}
```
`RSA-OAEP` is asymmetric - public key to encrypt and private to decrypt.
Can also be created using the `jwcrypto` python library.