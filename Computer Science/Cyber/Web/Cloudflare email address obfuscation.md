When you see an address like `/cdn-cgi/l/email-protection#413624232c203235243301272f32236f222e2c`
Or `<span class="__cf_email__" data-cfemail="hex">`
It's a cloudflare obfuscated email address.
The real email address is accessed by a simple one-byte xor encryption - the first byte is the xor key.