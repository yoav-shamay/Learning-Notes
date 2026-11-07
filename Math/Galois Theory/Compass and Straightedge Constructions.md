## Formal definition
We start with the points ${(0, 0), (1, 0)}$.
We can do the following actions:
- Construct a line through any 2 constructed points (denote as $\text{line}{(a, b)}$ for simplicity) 
- Construct a circle with its center at a constructed point and circumference passing through another constructed point (denote as $\text{circle}(\text{center}, \text{circumference point})$)
- Any intersection of 2 lines / circles / circle and line is also a constructed point (denote as $\text{intersection}(obj1, obj2)$)
## Constructible numbers
A real positive number $r$ is called constructible if there exists a construction of a segment of length $r$.
A negative number $r$ is called constructible if $|r|$ is constructible.
The set of constructible numbers is a sub-field of $\mathbb{R}$ and denoted as $\mathbb{R}_c$.
A number $x$ is constructible iff there are numbers $a_1, ..., a_n$ such that:
- $x \in \mathbb{Q}(\sqrt{a_1}, \sqrt{a_2}, ..., \sqrt{a_n})$
- $a_i \in \mathbb{Q}(\sqrt{a_1}, ..., \sqrt{a_{i - 1}})$ for all $1 \leq i \leq n$
Also every constructible number $x$ is algebraic of a power-of-2 degree over $\mathbb{Q}$.
## List of Constructions

### Constructing any natural multiple of a constructible number
Given a segment $AB$:
Construct $(A, C) = \text{intersection}(\text{circle}(B, A), AB)$
Then $AB = BC$, so $AC = 2AB$.
We can repeat this process:
Construct $(B, D) = \text{intersection}(\text{circle}(C, B), AB)$
Then $AB = BC = CD$, so $AD = 3AB$.
This process can be repeated any number of times to construct any natural multiple of a constructible number.
In particular starting from length 1, any natural number is constructible.
### Constructing perpendicular bisector of a segment
Given a segment $AB$.
Construct $c_1 = \text{circle}(A, B), c_2 = \text{circle}(B, A), (C, D) = \text{intersection}(c_1, c_2)$
Then $CD$ is the perpendicular bisector of $AB$.
### Constructing a perpendicular line to a segment passing through a point
Given a segment $AB$ and a point $C$
Assume WLOG $C \neq A$, we can always swap $A$ and $B$.
Construct $(A, D) = \text{intersection}(\text{circle}(C, A), AB)$
Then [[#Constructing perpendicular bisector of to a segment|construct the perpendicular bisector]] to $CD$.
### Constructing a parallel line to a segment passing through a point
Given a segment $AB$ and a point $C$ not in $AB$.
[[#Constructing a perpendicular line to a segment passing through another point|Construct a perpendicular line to AB passing through C]], denote it as $l$.
Then [[#Constructing a perpendicular line to a segment passing through another point|Construct a perpendicular line to l passing through C]].
This line is parallel to $AB$ and passes through $C$.
### Angle bisection
Given an angle $\measuredangle BAC$
Construct:
- $c_1 = \text{circle}(A,C)$
- $(A,D) = \text{intersection}(c_1, AB)$
- $c_2 = \text{circle}(C, A)$
- $c_3 = \text{circle}(D, A)$
- $(A, E) = \text{intersection}(c_2, c_3)$
Then $\measuredangle BAE = \measuredangle EAC = \frac{1}{2}\measuredangle BAC$
### Equilateral triangle (with any constructible side length)
Given a segment $AB$, construct:
- $c_1 = \text{circle}(A, B)$
- $c_2 = \text{circle}(B, A)$
- $(C, D) = \text{intersection}(c_1, c_2)$
$ABC$ and $ABD$ are equilateral triangles.
### Constructing a circle of a constructible radius through any point
Given a segment $AB$ and a point $C$, we construct a circle of radius $AB$ with its center at $C$.
Construct:
- [[#Constructing a parallel line to a segment passing through a point|A parallel line to AB passing through C]], denote it as $l$.
- [[#Constructing a parallel line to a segment passing through a point|A parallel line to AC passing through B]], denote it as $l_2$.
- $D = \text{intersection}(l, l_2)$
Then $CD = AB$, and therefore the answer is $\text{circle}(C, D)$
### Constructing sum of constructible numbers
Given 2 segments $AB, CD$
Construct:
- [[#Constructing a circle of a constructible radius through any point|A circle of radius AB passing through D]], denote it as $c$
- $(E, F) = \text{intersection}(CD, c)$. Assume $E$ is the point furtherer from $C$
Then $DE = AB$, $CE = CD + DE = CD + AB$
### Constructing product and ratio of constructible numbers
Given 3 constructible numbers $a, b, c$, we'll construct $ab/c$ (taking $c = 1$ will construct $ab$, $b = 1$ will construct $a/c$).
Start with any non-zero angle $\measuredangle XOY$, for example using [[#Constructing perpendicular bisector of to a segment|perpendicular bisector]].
Construct:
- [[#Constructing a circle of a constructible radius through any point|circle of radius c with center at O]], denote its intersection with $OX$ as $C$.
- [[#Constructing a circle of a constructible radius through any point|circle of radius b passing through O]], denote its intersection with $OX$ as $B$.
- [[#Constructing a circle of a constructible radius through any point|circle of radius a passing through O]], denote its intersection with $OY$ as $A$.
- [[#Constructing a parallel line to a segment passing through a point|parallel line to CA passing through B]], denote its intersection with $OY$ as $D$.
Then $OB/OC = OD/OA$, therefore $OD = ab/c$.
### Constructing the point with any constructible coordinates
Remember we have $O = (0, 0)$ and $A = (1, 0)$.
Given constructible numbers $x, y$, construct:
- [[#Constructing a circle of a constructible radius through any point|circle of radius x passing through O]], denote its intersection with $OA$ as $X = (x, 0)$
- [[#Constructing a perpendicular line to a segment passing through a point|perpendicular to OA passing through X]], denote it as $l$
- [[#Constructing a circle of a constructible radius through any point|circle of radius y passing through X]], its intersection with $l$ is the point $(x, y)$ 
### Constructing the square root of a constructible number
Given a constructible positive number $a$, construct:
- [[#Constructing sum of constructible numbers|the number]] $a+1$
- [[#Constructing product and ratio of constructible numbers|the number]] $(a + 1)/2$
- [[#Constructing the point with any constructible coordinates|the points]] $((a+1)/2, 0), (1, 0), (0, 0), (1, 1)$
- $(1,y_1), (1,y_2) = \text{intersection}(\text{circle}(((a + 1)/2, 0), (0, 0)), (1, 0)(1, 1))$
- Then $y_1, y_2 = \pm \sqrt{a}$, therefore $(1, y_1)(1, 0) = \sqrt{a}$.
This is because the circle is represented by the formula $(x - (a + 1)/2)^2 + y^2 = (a+1)^2 / 4$
Therefore if $x = 1$ we get $(a - 1)^2/4 + y^2 = (a + 1)^2/4$
Therefore $y^2 = ((a + 1)^2 - (a - 1)^2) / 4 = (4a) / 4 = a$.
## Proof sketch of constructible numbers characterization
From the constructions above, it can be shown that $R_c$ is at least the numbers shown in the characterization.
So all points of coordinates $(x, y)$ where $x, y$ are of the form are constructible.
Then the idea is to show that all possible constructions of new points (intersection of lines, circles, circle and line) all lead to points that are already in the set (not very interesting algebraic proof).
## Other impossible constructions
- You can't divide an angle by 3.
Proof sketch: an angle of $60 \degree$ is constructible, therefore an angle of $20\degree$ would be constructible.
Constructing a right triangle with this angle and side length 1 will construct a segment of length $\cos 20$.
This number has a minimal polynomial of degree 3 ($8x^3 - 6x - 1$) which isn't a power of 2.
- A regular n-gon is constructible iff $n = 2^k p_1...p_m$ where $k \geq 0$$, p_1,...,p_m$ are distinct Fermat primes (primes of the form $2^{2^x} + 1$)