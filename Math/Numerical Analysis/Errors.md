## Absolute and relative error
Denote the real value as $p$ and the approximation as $p^*$.
The absolute error is $|p - p^*|$.
The relative error is $|p - p^*| / |p|$ (if $p \neq 0$).
## Error Propagation
If we have computed $x \approx x_0$  and we want to compute $f(x) \approx f(x_0)$
Let's say $x = x_0 + \varepsilon$, $(f(x_0+\varepsilon)-f(x_0))/\varepsilon \approx f'(x_0)$
So the absolute error is about $|f'(x_0)|\varepsilon$.
And the relative error is about:
- $\delta f = \frac{\Delta f}{f(x)} \approx \frac{f'(x)\Delta x}{f(x)} = |\frac{f'(x)}{f(x)}x|\delta x$ 