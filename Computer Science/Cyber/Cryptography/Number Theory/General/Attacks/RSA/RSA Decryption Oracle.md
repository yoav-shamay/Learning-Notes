When you can decrypt any plaintext except a specific one $enc$, and you want to decrypt $enc$.
Option 1:
- Step 1: encrypt $c$ to find $C = 2^c$
- Step 2: decrypt $C * enc$ to find $dec * c$
- Step 3: divide answer by $c$ to find the plaintext
Option 2:
- Step 1: decrypt 2 to find $C = 2^d$
- Step 2: decrypt $enc / 2$ to find $dec / 2^d$
- Step 3: multiply both to find the plaintext