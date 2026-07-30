## The LWE Problem
The LWE problem is the following:
There's an unknown linear function $f: \mathbb{Z}_q^n \rightarrow \mathbb{Z}_q$, represented as $f(a) = (a, s)$ (standard inner product).  
A sample is a pair $(x, f(x) + e)$ where $x \in \mathbb{Z}_q^n$ and $e$ is a small error term with a known distribution.
This problem is believed to be hard.
## Encryption Schemes
This problem is used in encryption. In encryption, the message is encoded in the noise term.
When the secret key is known, $(A, S)$ can be just subtracted to obtain the noise term and get the plaintext.
For example, an encryption scheme can sample a random $A$, choose a value $\Delta$ such that $\Delta p < q$ (where $m < p$ for all $m$), and return $(A, ((A, S) + \Delta m + e) \% q)$ for random $-\Delta / 2 < e < \Delta / 2$.
Similarly, an encryption can also happen by making the large term random and the small term the message.
This encryption is homeomorphic - encryption of sum is the sum of ciphertexts (assuming the bounds are flexible enough so the error doesn't get larger than $q$).

In order to turn it to a public-key based encryption, the idea is to use this property - the public key is a bunch of encryptions of zero, to encrypt a plaintext you add a random subset of encryptions, and add $m$ to the error term.