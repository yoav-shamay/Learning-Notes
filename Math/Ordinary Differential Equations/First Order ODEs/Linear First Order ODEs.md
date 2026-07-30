[[First Order ODEs]] of the form $y' + a(x)y = b(x)$, over a range $(a, b)$ such that $a(x)$ and $b(x)$ are continuous on.
If $b(x) = 0$ then the equation is called homogenous.

The solutions are $e^{-A(x)} (\int{b(t)e^{A(t)}}dt + C)$ where $A(x) = \int a(t)dt$.
For homogenous equations it's $Ce^{-A(x)}$.
Given an initial condition it's easily solved by substituting $x_0$.

It has exactly one solution up to a constant, and exactly one solution given an initial condition.
This is over the entire range $(a, b)$ (which is stronger than the general [[First Order ODEs#Existence and Uniqueness Theorem|Existence and Uniqueness Theorem]] which only promises some range containing $x_0$)

The formula is derived by multiplying both sides by $e^{A(x)}$.
Then we get that the left hand side is $(y' + a(x)y)e^{A(x)} = (y e^{A(x)})'$ and the right hand side is $b(x)e^{A(x)}$.
Then we integrate both sides and divide by $e^{A(x)}$.