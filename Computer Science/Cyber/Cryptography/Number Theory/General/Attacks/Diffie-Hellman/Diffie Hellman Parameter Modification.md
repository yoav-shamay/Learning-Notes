You can intercept Diffie Hellman as man-in-the-middle by modifying keys sent to server/client.
Specifically you can do one of those:
- by modifying the public key each side sees to $p - 1$ or $0$, now both will see $s = 0$.
- by modifying the public key each side sees to $p$ or $1$, now both will see $s = 1$.
- By setting the base ($g$) to $0$ or $1$ or $p$ or $p-1$.
Now the secret will be just a known constant - $A$ or $B$ or $0$.
