## Many-one reduction
Also called Karp Reductions
A language $L$ is reducible to $L'$, also marked $L \leq L'$
If there's a computable function $f(x)$ that gets an input of $L$ and returns an input of $L'$, satisfying $w \in L \iff f(w) \in L'$
### Polynomial-time reduction
The same but $f(x)$ is computable in polynomial time
$L \leq_p L'$