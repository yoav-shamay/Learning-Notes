In many hashes, if you know `hash(a)`, `len(a)` and `b` then you can compute `hash(a | b)` where `|` is concat.
This is because the hash digest represents the entire internal state of the hash, which is computed by iterating on input blocks and each time changing the state based on it.
Note that usually padding is applied to the input blocks, so in `hash(a | b)` it actually means the hash of the **PADDED** `a` concat `b`.
## Applicable Hashes
Applicable to most hashes using the Merkle-Damgard construction, like [[MD5]], [[SHA256]] and SHA1.
## Performing
You can perform it using the `hash_extender` tool.
Url: https://github.com/iagox86/hash_extender
Alternatively, use the `length-extension-tool` PIP package.
Make sure to add the padding, `hash_extender` automatically does.