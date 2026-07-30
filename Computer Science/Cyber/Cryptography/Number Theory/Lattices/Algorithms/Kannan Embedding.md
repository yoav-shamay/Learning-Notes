An algorithm that reduces CVP to SVP.
No need to really know as sage does it by default when requesting CVP.
Given a lattice generated from $v_1, v_2, ..., v_n$ and a target vector $v$.
Requires that $v$ is close to the lattice (compared to the SVP of the lattice).
We define the lattice generated from $(v_1, 0), ..., (v_n, 0), (v, M)$ (zero is appended in the end of each lattice vector and $M$ is appended in the end of $v$).
Then we compute the SVP of the lattice. 
It most likely will be of the form $(a_1, ..., a_n, M)$ or $(a_1, ..., a_n, -M)$.
Then $(a_1, ..., a_n)$ is the difference vector from $v$ (if the last element is $-M$ it will be $(-a_1, ..., -a_n$))
Usually $M = 1$ is chosen, however in case that there's a smaller vector closer to $2v$ for example, a larger $M$ should be chosen to penalize choosing higher multiple of $v$ (however it will increase the chance that the SVP will just be independent of $v$ and it will return the SVP of the original lattice)