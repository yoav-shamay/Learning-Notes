An algorithm to compute the [[Osculating Polynomial]], including [[Hermite Polynomial]].
Exactly the same as [[Newton Interpolation]], where we replace each point with $m_i$ consecutive copies of it.
In addition we define $f[x_i,...,x_i] (n\ \text{times}) = f^{(n)}(x) / n!$ instead of the normal recurrence (as it will divide by zero).