This repository contains my lecture notes of Graph Theory Topic. </br>
-------------------------------------------------------------------------
**Table of Contents**
- [Lecture 1](#lecture-1)

# Lecture 1

Chapter 2: Basic Graph Terminologies from the textbook Basic Graph Theory by Md. Saidur Rahman.

### Graph Definition

- A graph $G$ is a tuple $(V, E)$ where:
    - $V$ is a finite set of **vertices** (nodes)
    - $E$ is a finite set of **edges** (each edge is an unordered pair of vertices)
  
- Notation:
    - Edge $e$ between vertices $u$ and $v$: $(u,v)$
    - Here $u$ and $v$ are also called the end-vertices of $e$
    - Vertex set: $V(G)$
    - Edge set: $E(G)$
  
- Size parameters:
    - $n = |V(G)|$ (number of vertices)
    - $m = |E(G)|$ (number of edges)

- Graph drawn as:
    - Vertices: points/circles
    - Edges: line segments/curves between vertices



### Graph Types

- **Simple graph**: No loops or multiple edges
<p align="center">
    <img src="Media\Lecture1\simple_graph.png" width="" /> <br/>
    <em>A simple graph with 11 vertices and 17 edges</em>
</p>

- **Multigraph**: May contain,
    - **Loops**: Edges with identical end-vertices
    - **Multiple edges**: More than 1 edges sharing the same vertex pair
<p align="center">
    <img src="Media\Lecture1\multi_graph.png" width="" /> <br/>
    <em>A multigraph having loops and multiple edges between the same pair of vertices</em>
</p>

- **Directed graph (digraph)**: Edges have direction
- **Weighted graph**: Weights assigned to vertices/edges
<p align="center">
    <img src="Media\Lecture1\directed_and_weighter_graph.png" width="" /> <br/>
</p>


### Key Relationships

- **Adjacency**: Vertices $u$ and $v$ are adjacent if connected by an edge
- **Incidence**: Edge $e = (u,v)$ is incident to vertices $u$ and $v$
- **Neighbors**: Vertices adjacent to a given vertex $v$
- **Degree** ($deg(v)$):
    - Number of edges incident to $v$
    - Loops count twice
    - Example: $deg(v_1) = 5$ in Fig. 2.1

#### Degree-Sum Formula (Lemma 2.2.1)

- **Statement**: For any graph $G = (V, E)$ with $m$ edges, the sum of all vertex degrees equals $2m$:

$$
\sum_{v \in V} \deg(v) = 2m
$$
- **Proof**:
    - Each **non-loop edge** connects two distinct vertices → contributes 1 to the degree of two vertices (total +2).
    - Each **loop edge** connects a vertex to itself → counted twice in that vertex's degree (total +2).
    - Thus, every edge adds exactly 2 to the total degree sum[^1].


##### Key Implications

- Also called the **"First Theorem of Graph Theory"** or **"Handshaking Lemma"**:
    - Analogous to handshakes: Each handshake involves two people → total handshakes must be even[^1].
- **Why it matters**: Provides a fundamental relationship between vertex degrees and edge count.


#### Corollary (Lemma 2.2.2)

- **Statement**: Every graph has an **even number of odd-degree vertices**.
- **Proof**:
    - Let $x$ = sum of even-degree vertices (even).
    - Let $y$ = sum of odd-degree vertices.
    - By Lemma 2.2.1: $x + y = 2m$ (even).
    - Since $x$ is even, $y = 2m - x$ must also be even.
    - For $y$ (sum of odd numbers) to be even, the *number of odd-degree vertices* must be even[^1].


##### Example

- In a graph with 5 vertices:
    - Degrees: {2, 2, 3, 3, 4} (sum = 14 → $2m = 14$ → $m = 7$ edges).
    - Odd-degree vertices: two (3 and 3), which is even.

<div style="text-align: center">⁂</div>










<!-- - Kadane's Algorithm
- String Pattern Searching
    - Rabin-Karp Algorithm
    - Knuth–Morris–Pratt algorithm
    - Aho-Corasick algorithm (and Trie Data Structure)
- Number Theory
    - Primality Test
        - Normal Aproach <!--https://progkriya.org/gyan/basic-number-theory->
        - Sieve of Eratosthenes
        - Goldbach's conjecture
    - Extended Euclid Algorithm
        - The Greatest Common Divisor (GCD) and Least Common Multiple (LCM)
        - Linear Modularity Equation Solver
    - Modular Exponentiation
    - Euler's Totient Function
        - Fermat's Test
        - Miller Rabin Test
- Fast Fourier Transform
- Travelling Sales Person Problem
- Computational Geometry 
-->



<!-- - Graph Theory
    - Traversal Algorithms
        - DFS
        - BFS
    - Single Source Shortest Path Algorithm
        - Dijkstra
        - BellmanFord
        - A* Search
    - All Pair Nodes Shortest Path Algorithms
        - Floyd-warshall algorithm
        - Johnson's algorithm
- Trees
    - Traversal
        - Inorder
        - Preorder
        - Postorder
    - AVL tree
    - Red-Black tree -->