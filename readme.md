This repository contains my lecture notes of Graph Theory Topic. The notes mostly follow the book *Basic Graph Theory by Md. Saidur Rahman*
</br>

-------------------------------------------------------------------------
**Table of Contents**
- [Lecture 1](#lecture-1)
    - [Graph Definition](#graph-definition)
    - [Basic Graph Types](#basic-graph-types)
    - [Key Relationships](#key-relationships)
      - [Maximum and Minimum Degree](#maximum-and-minimum-degree)
      - [Regular Graphs](#regular-graphs)
- [Lecture 2](#lecture-2)

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



### Basic Graph Types

- **Simple graph**: No loops or multiple edges
<p align="center" id="2.1">
    <img src="Media\Lecture1\simple_graph.png" width="" /> <br/>
    <em>Fig 2.1: A simple graph with 11 vertices and 17 edges</em>
</p>

- **Multigraph**: May contain,
    - **Loops**: Edges with identical end-vertices
    - **Multiple edges**: More than 1 edges sharing the same vertex pair
<p align="center">
    <img src="Media\Lecture1\multi_graph.png" width="" /> <br/>
    <em> Fig 2.2: A multigraph having loops and multiple edges between the same pair of vertices</em>
</p>

- **Directed graph (digraph)**: Edges have direction
- **Weighted graph**: Weights assigned to vertices/edges
<p align="center">
    <img src="Media\Lecture1\directed_and_weighter_graph.png" width="" /
    > <br/>
    <img src="Media\Lecture1\vertice_weighted_graph.png" width="" /
    > <br/>
    <em>Fig 2.3: Directed graph, Edge-Weighted graph and Vertice-weighted graph</em>
</p>

### Key Relationships

- **Adjacency**: Vertices $u$ and $v$ are adjacent if connected by an edge
- **Incidence**: Edge $e = (u,v)$ is incident to vertices $u$ and $v$
- **Neighbors**: Vertices adjacent to a given vertex $v$
- **Degree** ($deg(v)$):
    - Number of edges incident to $v$
    - Loops count twice
    - Example: $deg(v_1) = 5$ in <a href="#2.1">Fig. 2.1</a>
  
---

**Corollary 2.2.1: Degree-Sum Formula**: For any graph $G = (V, E)$ with $m$ edges, the sum of all vertex degrees equals $2m$: <br>

$$
\sum_{v \in V} \deg(v) = 2m
$$

<br>

- **Proof**:
    - Each **non-loop edge** connects two distinct vertices → contributes 1 to the degree of two vertices (total +2).
    - Each **loop edge** connects a vertex to itself → counted twice in that vertex's degree (total +2).
    - Thus, every edge adds exactly 2 to the total degree sum.

- Also called the **"First Theorem of Graph Theory"** or **"Handshaking Lemma"**:
    - Analogous to handshakes: Each handshake involves two people → total handshakes must be even.
- **Why it matters**: Provides a fundamental relationship between vertex degrees and edge count.

---

**Corollary 2.2.2**: Every graph has an **even number of odd-degree vertices**. <br>
- **Proof**:
    - Let $x$ = sum of even-degree vertices (even).
    - Let $y$ = sum of odd-degree vertices.
    - By Lemma 2.2.1: $x + y = 2m$ (even).
    - Since $x$ is even, $y = 2m - x$ must also be even.
    - For $y$ (sum of odd numbers) to be even, the *number of odd-degree vertices* must be even.

- **Example**: In the following graph with 5 vertices:
    - Degrees of each node: {1→2, 2→2, 3→3, 4→3, 5→4}
    - Summation of the degrees of the vertices = $7*2 = 14$
    - Odd-degree vertices: two (3 and 3), which is even.
<p align="center">
    <img src="Media\Lecture1\example_graph.png" width="" />
</p>

---

#### Maximum and Minimum Degree

- **Maximum degree (Δ(G))**: The highest number of edges connected to any single vertex in the graph.
    - *Example*: In <a href="#2.1">Fig. 2.1</a>, Δ(G) = 5 (vertex v<sub>1</sub> has the highest degree).
- **Minimum degree (δ(G))**: The lowest number of edges connected to any vertex.
    - *Example*: In <a href="#2.1">Fig. 2.1</a>, δ(G) = 1 (e.g., vertex v<sub>8</sub> with only one edge).
- **Average degree**: For a graph with $n$ vertices and $m$ edges, the average degree is $\frac{2m}{n}$.
    - *Why?*: Sum of all degrees is $2m$ (Degree-Sum Formula), so average is total divided by $n$.
    - *Key inequality*: $\delta(G) \leq \frac{2m}{n} \leq \Delta(G)$.


#### Regular Graphs

A graph is **regular** if all vertices have the *same degree*. Specific types include:

- **k-regular graphs**: Every vertex has degree $k$.
    - **0-regular**: No edges (isolated vertices).
    - **1-regular**: Disjoint edges (no shared vertices), like a matching.
    - **2-regular**: Consists of cycles (e.g., Fig. 2.4a).
        - *Simple cycle*: Vertices form a closed loop (e.g., triangle, square).
    - **3-regular (cubic graphs)**:
        - Widely known as ***Petersen graph*** (Fig. 2.4b): 10 vertices, 15 edges.
        - It is a small, simple-looking graph that breaks a lot of the usual rules in graph theory. It is often used as a "counterexample"
    - **5-regular**:
        - *Doughnut graphs* (Fig. 2.4d): $4p$ vertices for parameter $p$.
    - **d-dimensional hypercube** (Fig. 2.4c):
        - $2^d$ vertices, each of degree $d$.
        - *Example*: 4D hypercube has 16 vertices, each connected to 4 others.

<p align="center">
    <img src="Media\Lecture1\k_regular_graphs.png" width="" />
</p>

---

**Corollary 2.2.3:** Every regular graph with an odd degree has an even number of vertices. <br>
- **Proof**:
  - **Handshaking Lemma**: In any graph, the sum of all vertex degrees equals twice the number of edges. This sum is always **even** because it's $2 \times \text{edges}$
  - **Regular graph property**: If a graph is $k$-regular, every vertex has degree $k$. Thus, the sum of degrees is $n \times k$ (where $n = \text{number of vertices}$).
  - **Odd $k$ constraint**: If $k$ is odd, then $n \times k$ must be even (per the handshaking lemma).
  - **Key insight**: An odd number ($k$) multiplied by another number ($n$) only gives an even result if $n$ is **even**. Thus, $n$ must be even when $k$ is odd.

**Example**:

- A 3-regular graph (cubic graph) with an odd degree must have an even number of vertices (e.g., the Petersen graph has 10 vertices).

<p align="center">
    <img src="Media\Lecture1\The-Petersen-graph.png" width="300" /> <br>
    <em>Petersen graph</em>
</p>


---

**Corollary 2.2.4:** A $k$-regular graph with $n$ vertices has $\frac{nk}{2}$ edges. <br>

- **Sum of degrees**: In a $k$-regular graph, the sum of all vertex degrees is $n \times k$ (since each of $n$ vertices has degree $k$).
- **Handshaking Lemma**: This sum also equals $2 \times \text{edges}$ (denoted $2e$).
- **Equation**: $n \times k = 2e$.
- **Solve for edges**: Rearrange to get $e = \frac{n \times k}{2}$.

**Example**:

- A 3-regular graph with 4 vertices has $\frac{4 \times 3}{2} = 6$ edges
<p align="center">
    <img src="Media\Lecture1\example_2.2.4.png" width="" />
</p>


<!-- <div style="text-align: center">⁂</div> -->



# Lecture 2
To be added






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