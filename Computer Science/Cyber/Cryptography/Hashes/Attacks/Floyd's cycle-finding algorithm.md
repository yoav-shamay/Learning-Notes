Also called the tortoise and hare.
A low-memory birthday attack alternative.
Allows to find a cycle in $f: S \rightarrow S$ in $O(\sqrt{|S|})$ time and $O(1)$ memory.
This also allows to find a collision.

The expected cycle size is $|S|$.
We'll start with two pointers $x = y = \text{<some initial starting value>}$
And repeatedly swap:
- $x = f(x)$
- $y = f(f(y))$
In $O(\text{cycle size})$, which is $O(\sqrt{|S|})$, they will meet.

Then start one pointer from this meeting point and one pointer at the starting value again.
Advance both pointers by 1 every time they will meet exactly at the starting point of the cycle.
The previous value of each pointer at this meeting point will form a collision (one will arrive from the initial chain and one from the cycle).

This is because if the chain is of size $x$ and the cycle of size $y$, the amount of steps $t$ satisfies $y | 2t - x - (t - x)$ which means $y | t$, which means $y | (y + x) - x$, so they will meet at the starting point. 
## Implementation
TODO