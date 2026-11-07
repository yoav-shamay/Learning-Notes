[[Linear ODEs]] of order one, which means $y' + a(x)y = b(x)$.

The solutions are $e^{-A(x)} (\int{b(t)e^{A(t)}}dt + C)$ where $A(x) = \int a(t)dt$.
For homogenous equations it's $Ce^{-A(x)}$.

Given an initial condition it's easily solved by substituting $x_0$.

The formula is derived by multiplying both sides by $e^{A(x)}$.
Then we get that the left hand side is $(y' + a(x)y)e^{A(x)} = (y e^{A(x)})'$ and the right hand side is $b(x)e^{A(x)}$.
Then we integrate both sides and divide by $e^{A(x)}$.