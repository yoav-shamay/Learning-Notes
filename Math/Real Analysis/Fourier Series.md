Given a $2L$ periodic function $f$ integrable in $[-L, L]$ (or a function that can be extended to this)
The Fourier series of $f$ is:
$$
f(x) \sim \frac{a_0}{2} + \sum_{n = 1}^{\infty}(a_n \cos{\frac{n \pi x}{L}} + b_n \sin{\frac{n \pi x}{L}})
$$

where:
$$
\begin{matrix}
a_n = \frac{1}{L}\int_{-L}^L f(t) \cos{\frac{n \pi t}{L}} dt \\
b_n = \frac{1}{L}\int_{-L}^L f(t) \sin{\frac{n \pi t}{L}} dt
\end{matrix}
$$
Note that it doesn't always converge to $f$ (or converges to all).
## Properties
- If $f$ is odd then $a_n = 0$ (the summation only contains $\sin$ terms)
- If $f$ is even then $b_n = 0$ (the summation only contains $\cos$ terms)
## Complex Representation
The Fourier series can also be represented as the following:
$$
f(x) \sim \sum_{n = -\infty}^{\infty} c_n e^{in \pi x}/L
$$
where:
$$
c_n = \frac{1}{2L} \int_{-L}^L f(x) e^{-in \pi x / L} dx
$$
Also:
- $\overline{c_n} = c_{-n}$
- $c_0 = \frac{1}{2}a_0$
- $c_n = \frac{1}{2}(a_n - ib_n) \text{ for } n \geq 1$
## Mathematical Results
### Basel Inequality
Given $f$ piecewise continuous on $[-L, L]$, the series
$$
\frac{1}{2} a_0^2 + \sum_{n = 1}^{\infty} (a_n^2 + b_n^2)
$$converges, and its limit is less than and equal to
$$
\frac{1}{L} \int{-L}^L f^2(x) dx
$$
### Riemann–Lebesgue lemma
If $f$ is piecewise continuous in $[-L, L]$:
$$
\lim_{n \to \infty} \int_{-L}^L f(x) \cos{\frac{n \pi x}{L}} dx = 0
$$
$$
\lim_{n \to \infty} \int_{-L}^L f(x) \sin{\frac{n \pi x}{L}} dx = 0
$$
## Convergence (Fourier Theorem)
Given $f$ piecewise continuous with period $2L$ and $x_0 \in \mathbb{R}$ such that $f$ is continuous in $x_0$ and both directional derivatives of $f$ exist in $x_0$, then the Fourier series of $f$ at $x_0$ converges to $f(x_0)$ 
or alternatively, if $f$ isn't continuous in $x_0$, then the Fourier series of $f$ at $x_0$ converges to:
$$
\frac{f(x_0 + 0) + f(x_0 - 0)}{2}
$$
## Uniform Convergence
If $f$ is periodic with period $2L$, $f$ is continuous and $f'$ is piecewise continuous in $\mathbb{R}$, then the Fourier series of $f$ converges absolutely and uniformly to $f$ in $\mathbb{R}$.
## Mean Convergence and Parseval Identity
Given $f$ piecewise continuous in $[-L, L]$, denote $S_n(f)(x)$ as the $n$-th partial sum of the Fourier series at $x$. then:
$$
\lim_{n \to \infty} \int_{-L}^L (f(x) - S_n(f)(x))^2 dx = 0
$$
If and only if:
$$
\frac{1}{2} a_0^2 + \sum_{n = 1}^{\infty}(a_n^2 + b_n^2) = \frac{1}{L}\int_{-L}^L f^2(x) dx
$$

The first expression is called the mean error of the approximation, so this means that the mean error converges to 0, or that the Fourier Series converges on mean to $f$ in $[-L, L]$.
The second expression is called the Parseval Identity.
If $f$ is periodically continuous in $[-L, L]$, both expressions are satisfied.
## Fejer Sums
The n-th Fejer sum is defined as the mean of the first n + 1 partial sums:
$$
\sigma_n(f)(x) = \frac{1}{n + 1}\sum_{k = 0}^n S_k(f)(x)
$$
If $f$ is continuous and $2L$-periodic, then its Fejer sums converges uniformly to $f$ on $\mathbb{R}$.
