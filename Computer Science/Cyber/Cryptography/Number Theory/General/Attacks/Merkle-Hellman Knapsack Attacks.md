Denote the public key as $a_1, ..., a_n$ and the private key as $b_1, ..., b_n$ with multiplier $r$ and modulo $M$.
Denote the ciphertext as $e$.
## Attack 1 - Solving subset sum using LLL
The idea is to generate the following lattice:
$$
\begin{pmatrix}
1 && 0 && \dots && 0 && 0 && a_1 \\
0 && 1 && 0 && \dots && 0 && a_2 \\
&& && && \dots \\
0 && \dots && 0 && 0 && 1 && a_n \\
0 && \dots && 0 && 0 && 0 && e
\end{pmatrix}
$$
The shortest vector will most likely be minus one on the chosen elements, and zero in the end. Use LLL to find it (it will be shortest by a large margin)
Solves subset sum in general for low element density (where $n$ is smaller than $\log_2$ of the target, as there are $2^n$ possible solutions and it needs to be the only close sum).
## Attack 2 - Finding long superincreasing sequence using LLL
https://pmc.ncbi.nlm.nih.gov/articles/PMC12118879/pdf/pone.0322726.pdf
The idea is to use the lattice generated from the following matrix:
$$
\begin{pmatrix}
-a_1 && 0 && \dots && 0 && 0 \\
0 && -a_1 && 0 && \dots && 0 \\
&& && \dots \\
0 && \dots && 0 && 0 && -a_1 \\
a_2 && a_3 && \dots && a_{n - 1} && a_n
\end{pmatrix}
$$
Denote $S = S_2, ..., S_n$ where $S_i = (b_1 a_i - b_i a_1)/M$.
Denote $b_i = W^{-1}a_i + Mk_i$, then $S_i = k_1 a_i - k_i a_1$.
It can be proven that all $S$ are much smaller than $M$.
Therefore $S$ is in the lattice and is most likely the shortest vector.
So we can run LLL and get $S$ and the $k$ values from the transformation matrix.
We also get that $a_i * k_1 \equiv S_i \pmod{a_1}$ (because $S_i = k_1 a_i - k_i a_1$ and $S_i$ is small, so less than $a_1$)
Therefore we can multiply 
It can be proven that there exists a small $i$ such that $S_i, ..., S_n$ is a superincreasing sequence A superincreasing sequence is a sequence where each element is bigger than the sum of all previous ones, so knapsack can be trivially solved on it by going from last to first and choosing (and subtracting) the current element if the current element is smaller than the remaining sum.
Therefore we can brute force whether we choose the first $i - 1$ elements, replace $e$ with $e - \sum \text{chosen elements}$, then replace $e$ with $(e \cdot k_1) \mod a_1$.
Then we solve knapsack on the superincreasing $S_i, ..., S_n$ and decrypt the ciphertext.
## Attack 3 - ILP by Adi Shamir
The first attack from 1984
TODO write