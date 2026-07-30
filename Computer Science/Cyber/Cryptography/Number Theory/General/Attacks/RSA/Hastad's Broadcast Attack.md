An attack on RSA.
It is applicable when you have `e` ciphertexts of the same plaintext with different values of `n`.
It is assumed that the values of `n` are coprime. If not, factoring is easy using `gcd`.
## The Attack
Denote the plaintext as $M$, the exponent as $e$, the moduli as $n_1,n_2,...,n_e$  and the ciphertexts as $c_1,c_2,...,c_e$.
Then we can find the solution $C$ to the following system of equations using CRT:
$$
\begin{matrix}
C \equiv ct_1 \pmod{n_1} \\
C \equiv ct_2 \pmod{n_2} \\
... \\
C \equiv ct_e \pmod{n_e}
\end{matrix}
$$
Then this is satisfied $M^e \equiv C \pmod{n_1*n_2*...*n_e}$.
As $n_1*n_2*...*n_e > M^e$, we can then find $M$ by just taking the $e$-th root of $C$.
If the plaintext is smaller than $n$ the actual needed quantity is $e \times \text{bytecnt}(pt) / \text{bytecnt}(n)$
## Generalization - padding or polynomial
If instead of $pt^e \pmod{n_i}$ we are given $p_i(pt)^e \pmod{n_i}$, where $p_i(x)$ can differ between ciphertexts (but it doesn't have to) and all $n_i$ are different (if there are 2 equal $n$ with different polynomials you can use [[Franklin-Reiter Attack]]).
If we are given $e \times \max{\deg{p_i(x)}}$ ciphertexts, we can still recover $pt$.
Denote we are given $C_i \equiv p_i(pt)^e \pmod{n_i}$ for $1,..,m$
Denote $n = n_1 \times ... \times n_m$
Then we will find $p(x) \equiv p_i(x)^e - C_i \pmod{n_i}$, where $p(x)$ is mod $n$, by running CRT on every coefficient.
Now we have polynomial $p(x)$ of degree $e \times \max{\deg{p_i(x)}}$ mod $n$ with $pt$ as root.
Because $pt < n^{1/\deg{p(x)}}$, we can use [[Coppersmith Method]] to find this root.
If the plaintext is smaller than $n$ the actual needed quantity is $e \times \max{\deg{p_i(x)}} \times \text{bytecnt}(pt) / \text{bytecnt}(n)$