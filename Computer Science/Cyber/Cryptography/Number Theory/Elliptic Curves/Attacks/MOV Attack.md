The idea is to use [[Weil Pairing]] to reduce ECDLP (Elliptic Curve Discrete Log Problem) to normal numbers discrete log, which can be solved more efficiently (but still not polynomial).
If we have $G$ and $kG$, where $\text{ord}(G) = r$, find $G_2$ such that $e_r(G, G_2) \neq 1$ (shouldn't be difficult, TODO details).
Then solve discrete log on $e_r(G, G_2)$ and $e_r(kG, G_2) = e_r(G,G_2)^k$
This is only viable if the embedding degree of the curve is small.
See [[Weil Pairing#On Finite Fields]] for more details.