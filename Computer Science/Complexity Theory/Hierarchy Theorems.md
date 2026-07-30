Very similar, but time has an extra log factor that it has to be lower.
## Time Hierarchy Theorem
### Time constructible function
A function $f(n)$ is said to be space-constructible if there's a Turing Machine $M$ that gets $n$ in unary representation and computes $f(n)$ in $O(f(n))$ time.
Most functions, as long as it's not too small.
### Theorem
For every space constructible function $f(n)$, there's a language $L$ decidable in time $O(f(n))$ but not in $o(f(n)/\log f(n))$.
This means for every function $g(n) \in o(f(n)/\log f(n))$, $TIME(g(n)) \subset TIME(f(n))$
### Conclusions
- $TIME(n^{\epsilon_1}) \subset TIME(n^{\epsilon_2}) \text{ for real } \epsilon_1 < \epsilon_2$
- $P\subset EXPTIME$
## Space Hierarchy Theorem
### Space constructible function
A function $f(n)$ is said to be space-constructible if there's a Turing Machine $M$ that gets $n$ in unary representation and computes $f(n)$ in $O(f(n))$ space.
Most functions, as long as it's not too small.
### Theorem
For every space constructible function $f(n)$, there's a language $L$ decidable in space $O(f(n))$ but not in $o(f(n))$.
This means for every function $g(n) \in o(f(n))$, $SPACE(g(n)) \subset SPACE(f(n))$
### Conclusions
- $SPACE(n^{\epsilon_1}) \subset SPACE(n^{\epsilon_2}) \text{ for real } \epsilon_1 < \epsilon_2$
- $PSPACE \subset EXPSPACE$