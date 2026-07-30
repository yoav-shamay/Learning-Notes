## Definition
Languages $L$ that are in NP, and every language $L' \in NP$ satisfies $L' \leq_P L$
In other words, every language in NP is polynomial time reducible to them (using [[Reductions#Many-one reduction]])
## P = NP
If there's an NP complete language L satisfying $L \in P$, then $P = NP$ 
## List
- $SAT$
- $3SAT$
- $UHAMPATH$ - undirected Hamiltonian path
- $HAMPATH$ - directed Hamiltonian path
- $HAMCYCLE$ - Hamiltonian cycle
- $TSP$ - traveling salesman problem, min weight Hamiltonian cycle in weighted complete graph
- $CLIQUE$ - largest Clique in graph
- $VERTEX-COVER$ - min vertex cover of graph (minimum vertices covering all edges)
- $SUBSET-SUM$ - whether there's a subset with a specific sum
- $IS$ - largest independent set (set of vertices where no 2 vertices are connected by an edge) in graph. basically anti-clique