A method for accelerating convergence of linearly converging sequences.
This method assumes the elements are in one side of the limit (either always smaller or always larger).
The idea is that because the convergence order is 1 then $(p_n - p) / (p_{n - 1} - p) \approx (p_{n - 1} - p) / (p_{n - 2} - p)$
Therefore we can derive that $p \approx p_n - (p_n - p_{n - 1})^2 / (p_n - 2p_{n - 1} + p_{n - 2}) = (\Delta p_n)^2 / \Delta^2 p_n = \hat{p}_n$.
This new sequence satisfies $\lim_{n\to\infty} (\hat{p}_n - p) / (p_n - p) = 0$, meaning that it converges faster than $p_n$.
Sometimes it will be worse in the beginning and we will want to replace after a few iterations (as it's based on limit and stuff that's eventually true).
When used to accelerate iterative methods (like the fixed point method), it's probably better to compute the next values in the recurrence formula based on $\hat{p}_n$ instead of $p_n$ as it converges faster (like computing $p_{n + 1} = g(\hat{p_n})$ instead of $p_{n + 1} = g(p_n)$).
