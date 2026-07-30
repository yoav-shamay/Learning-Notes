Defined for every prime $p$ (it's a parameter).
## The p-adic valuation
Denoted as $v_p(x)$.
For non-zero integer, $v_p(x)$ is the largest power of $p$ dividing $x$ (the largest $n$ such that $p^n | x$ and $p^{n+1} \nmid x$).
For zero, $v_p(0) = \inf$.
For a fraction, $v_p(a / b) = v_p(a) - v_p(b)$.
## The p-adic absolute value function
A different absolute value function for rational numbers.
Defined as $|x|_p = p^{-v_p(x)}$ (for $x = 0$ it's $0$). 
This function induces a metric, $d_p(x, y) = |x - y|_p$.
## The p-adic numbers
$\mathbb{Q}_p$ is the completion field (as in every cauchy sequence converges) of $\mathbb{Q}$ under the p-adic absolute value function.
They can be uniquely represented as infinite series:
$$
\sum_{i=-n_0}^{\infty}a_i p^i = a_{-n_0}p^{-n_0} + a_{-n_0+1}p^{-n_0+1} + ... + a_0p^0 + a_1p^1 + ...
$$
where $0 \leq a_i < p$.
This representation is called the p-adic representation.
It can actually start from a positive index, it's written like that to signify that it can have negative exponents.
For this number, assuming $a_{-n_0} \neq 0$, the absolute value is $p^{n_0}$.
This is similar to base-p representation for real numbers, but the infinite direction is for positive exponents instead of negative (as higher exponents of $p$ has smaller absolute value under this metric).
## The p-adic integers
The p-adic integers are defined as following: $\mathbb{Z}_p = \{x \in Q_p \mid |x|_p \leq 1\}$.
Alternatively, it can be defined as the completion of $\mathbb{Z}$ (similarly to the definition of $\mathbb{Q}_p$).
In the series representation, those are all numbers where there are no negative $p$ exponents.
It's a ring.
## Properties
- The only absolute values on $\mathbb{Q}$ are the normal one and the p-adic ones (up to equivalence).
- $|x + y|_p \leq \text{max}(|x|, |y|)$ (this is called a non-archimedean absolute value function)
- If $|x|_p \neq |y|_p$, $|x+y|_p = \text{max}(|x|, |y|)$
- $d_p(x, z) \leq \text{max}(d_p(x, y), d_p(y, z))$ (this is called an ultrametric space).
- A series $\sum_{n=0}^{\infty} a_n$ converges iff $a_n$ converges to zero.
## p-adic integer modulo power of p
You can take any p-adic integer modulo any power of $p$, to get an integer mod $p^n$.
This is done by trimming all powers of $p$ at least the modulo in the representation.
It preserves addition and multiplication.
Formally, it's an isomorphism between $\mathbb{Z}_p / p^n \mathbb{Z}_p$ and $\mathbb{Z} / p^n \mathbb{Z}$.
Alternatively, an homomorphism between $\mathbb{Z}_p$ and $\mathbb{Z} / p^n \mathbb{Z}$.