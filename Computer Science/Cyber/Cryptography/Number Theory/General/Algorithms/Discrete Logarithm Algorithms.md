Given a group G, $a$ and $a^k$, find $k$.
Mostly used as log in modulo.
## Baby-Step Giant-Step Algorithm
Input: $base$, $element$, $G$, $order$
$order$ is any upper bound for the order of $a$, can be the order of the element, of the group or even $mod - 1$ in case of $\mathbb{Z}_{mod}$
Time and space complexity: $O(sqrt(order))$

The idea is simple meet in the middle - if the result is $a * m + b$, we save all powers smaller than `m` (options for b) and divide by $a^m$ until we get $a^x, x < m$, than we know $x$ by the powers we saved.
### Algorithm
Denote $m=ceil(sqrt(order(G)))$
Memorize in hashmap $a^x : x$ for $0\leq x < m$
Find $d = a^{-m}$
Save $res=0$
Repeat until $element$ is in the hashmap:
	Multiply $element$ by $d$
	Add 1 to $res$
Return $res * m + hashmap[res]$
## Pohlig-Hellman algorithm
Used when the order of the group is smooth, it has only small factors.
This mean $p-1$ is smooth when used in multiplication mod $p$.
Implemented in sage (default when doing logarithm)
TODO write algorithm