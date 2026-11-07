An expression of the form:
![[Continued Fractions Image.png]]
Where $a$ and $b$ are integer sequences.
Every irrational number has an infinite continued fraction expansion.
Rational numbers have a finite representation.
## Simple Continued Fractions
Simple continued fractions are continued fractions where all $a$ are 1, and $b_i \geq 1$ for $i > 0$.
For now on, we'll rename the sequence $b$ to $a$ for simplicity.
Also by convention the last term is $\geq 2$ (for uniqueness).
Every real number has unique continued fraction approximation, generated using the following recurrence:
$$
\begin{matrix}
x_0 = x \\
a_n = \lfloor x_n \rfloor \\
x_{n + 1} = \frac{1}{x_n - a_n}
\end{matrix}
$$
$a_i$ is the $i$-th coefficient, and $x_i$ is the tail of the approximation ($x_i = a_i + \frac{1}{a_{i + 1} + ...}$)
### Rational $x$
For rational numbers, this construction will always stop (reaching exact value, with $x_i = a_i$).
The construction ends up being exactly the Euclidean algorithm.
Denote $x_i = \frac{p_i}{q_i}$.
For $i$:
Denote $p_i = n q_i + m$.
Then $a_i = n$ and:
$$
x_{i + 1} = \frac{1}{x_i - a_i} = \frac{1}{\frac{p_i}{q_i} - n} = \frac{q_i}{p_i - nq_i} = \frac{q_i}{m} 
$$
So each step we swap $p, q$ with $q, (p \% q)$ which is exactly the Euclidean algorithm.
### Generating Partial Approximation Fractions
The partial approximations $\frac{b_n}{c_n}$ are generated using:
$$
\begin{matrix}
b_{-2} = 0 \\
b_{-1} = 1 \\
c_{-2} = 1 \\
c_{-1} = 0 \\
b_i = a_i \times b_{i - 1} + b_{i - 2} \\
c_i = a_i \times c_{i - 1} + c_{i - 2}
\end{matrix}
$$
#### Proof
This is proved using induction.
Base case:
$$
\begin{matrix}
\frac{b_0}{c_0} = \frac{a_0}{1} \\
\frac{b_1}{c_1} = \frac{a_1 a_0 + 1}{a_1} = a_0 + \frac{1}{a_1}
\end{matrix}
$$
Step - Assume:
$$
\frac{b_n}{c_n} = \frac{a_n b_{n - 1} + b_{n - 2}}{a_n c_{n - 1} + c_{n - 2}}
$$
is the correct fractional representation with coefficient sequence $a_0, ..., a_n$, for every real positive $a_1, ..., a_n$.
Then for $n + 1$, in the fraction, $a_n$ is replaced with $a_n + \frac{1}{a_{n + 1}}$
Therefore:
$$
\frac{b_{n + 1}}{c_{n + 1}} = \frac{a_n b_{n - 1} + b_{n - 2} + \frac{b_{n - 1}}{a_{n + 1}}}{a_n c_{n - 1} + c_{n - 2} + \frac{c_{n - 1}}{a_{n + 1}}} = \frac{b_n + \frac{b_{n - 1}}{a_{n + 1}}}{c_n + \frac{c_{n - 1}}{a_{n + 1}}} = \frac{a_{n + 1}b_n + b_{n - 1}}{a_{n + 1}c_n + c_{n - 1}}
$$

### Legendre's Theorem
For any real $x$, a reduced fraction $\frac{p}{q}$ such that $|x - \frac{p}{q}| < \frac{1}{2q^2}$ then $\frac{p}{q}$ must be a convergent in the simple continued fraction expansion for $x$.
This means that $\frac{p}{q}$ is an element in the sequence
$$
a_0, a_0 + \frac{1}{a_1}, a_0 + \frac{1}{a_1 + \frac{1}{a_2}}, ...
$$
Where $a_n$ are the coefficients in the unique simple continued fraction expansion of $x$.