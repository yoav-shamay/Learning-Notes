Let there be a sequence of independent random variables with same expectation $X_1, X_2, ...$
and $T$ be a stopping time where $T \geq n$ depends only on $X_1, ..., X_{n-1}$ (we decide to stop only based on the current and past observed values and not the next ones).
Then $E[\sum_{i=1}^{T} X_i] = E[T]E[X_i]$.
## Example
Let's say we roll dice until we get 6, and want to find the expected sum of all rolls.
Then $E[X_i] = 3.5$ and $E[T] = 1/\frac{1}{6} = 6$ so the expectation is $3.5 * 6 = 21$.
