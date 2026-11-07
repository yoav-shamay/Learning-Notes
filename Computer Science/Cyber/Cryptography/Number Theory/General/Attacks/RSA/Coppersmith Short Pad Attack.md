Given $p(a, b)$ and $q(a, b)$ and a small $b$, recovers $a, b$.
This is applicable for example for $x^e$ and $(x + b)^e$ where $b$ is small, which is the case for same message with 2 distinct short paddings.
## The Attack
Take the following polynomials:
- $f(x) = p(x) - p(a)$
- $g(x, y) = q(x, y) - q(a, b)$
$f(x)$ and $g(x, b)$ has a common root.
It means the [[Resultant]] $\operatorname{Res}(f, g)$ has $b$ as a (small) root.
Then you can use [[Coppersmith Method]] to find $b$.
## The Exact Bound
The bound is $b < n^{1 / \deg{\operatorname{Res}(f, g)}}$.
Denote $D = \deg{\operatorname{Res}(f, g)}$.
Then: TODO D bound
