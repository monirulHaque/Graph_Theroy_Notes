This repository contains my lecture notes of Graph Theory Topic. The notes mostly follow the book *Basic Graph Theory by Md. Saidur Rahman*
</br>

-------------------------------------------------------------------------
**Table of Contents**
- [Chapter 2](#chapter-2)
    - [Graph Definition](#graph-definition)
    - [Basic Graph Types](#basic-graph-types)
    - [Key Relationships](#key-relationships)
      - [Lemma 2.2.1](#lemma-221)
      - [Lemma 2.2.2](#lemma-222)
      - [Maximum and Minimum Degree](#maximum-and-minimum-degree)
      - [Regular Graphs](#regular-graphs)
    - [Corollary 2.2.3](#corollary-223)
    - [Corollary 2.2.4](#corollary-224)
    - [Subgraphs](#subgraphs)
    - [Key Graph Classes](#key-graph-classes)
      - [1. Null Graphs](#1-null-graphs)
      - [2. Complete Graphs](#2-complete-graphs)
      - [3. Bipartite Graphs](#3-bipartite-graphs)
      - [4. Path Graphs](#4-path-graphs)
      - [5. Cycle Graphs](#5-cycle-graphs)
      - [6. Wheel Graphs](#6-wheel-graphs)
    - [Operations on Graphs](#operations-on-graphs)
      - [Union of Graphs](#union-of-graphs)
      - [Intersection of Graphs](#intersection-of-graphs)
      - [Complement of Graphs](#complement-of-graphs)
      - [Corollary 2.5.1](#corollary-251)
      - [Subdivisions](#subdivisions)
      - [Edge Contraction](#edge-contraction)
    - [Graph Isomorphism](#graph-isomorphism)
    - [Corollary 2.6.1](#corollary-261)
    - [Degree Sequence](#degree-sequence)
      - [Testing if a sequence is graphic](#testing-if-a-sequence-is-graphic)
    - [Graph Representation](#graph-representation)
- [Chapter 3](#chapter-3)
    - [Walks](#walks)
    - [Trails](#trails)
    - [Paths](#paths)
    - [Cycles](#cycles)
      - [Lemma 3.1.1](#lemma-311)
    - [Graph Connectivity/Connected Components](#graph-connectivityconnected-components)
      - [Lemma 3.1.2](#lemma-312)
      - [Lemma 3.1.3](#lemma-313)
    - [Cut-Edges](#cut-edges)
      - [Lemma 3.1.4](#lemma-314)

# Chapter 2

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
- **Degree** ( $deg(v)$ ):
    - Number of edges incident to $v$
    - Loops count twice
    - Example: $deg(v_1) = 5$ in <a href="#2.1">Fig. 2.1</a>
  
---

#### Lemma 2.2.1
**Statement**: For any graph $G = (V, E)$ with $m$ edges, the sum of all vertex degrees equals $2m$: <br>

$$
\sum_{v \in V} \deg(v) = 2m
$$

<br>

- **Proof**:
    - Each **non-loop edge** connects two distinct vertices → contributes 1 to the degree of two vertices (total +2).
    - Each **loop edge** connects a vertex to itself → counted twice in that vertex's degree (total +2).
    - Thus, every edge adds exactly 2 to the total degree sum.

<br>

- Also called **"the Degree-Sum Formula"**, **"First Theorem of Graph Theory"** or **"Handshaking Lemma"** :
    - Analogous to handshakes: Each handshake involves two people → total handshakes must be even.
- Why it matters and it's applications: 
  - Provides a fundamental relationship between vertex degrees and edge count.
  - **Algorithm Optimization:** Verify edge-count integrity in graph algorithms (e.g., during graph loading in network analysis tools). If `sum(degrees) != 2m`, data is corrupted.
  - **Network Analysis:** Calculate **network density** in social/media graphs: `density = m / (n(n-1)/2)` requires knowing `m` via `sum(deg)/2`.
  - **Data Validation:** In graph databases, use as a sanity check for ETL processes (e.g., Neo4j/Cypher queries).

---

#### Lemma 2.2.2
**Statement**: Every graph has an **even number of odd-degree vertices**. <br>
- **Proof**:
    - Let $x$ = sum of even-degree vertices (even).
    - Let $y$ = sum of odd-degree vertices.
    - By Lemma 2.2.1: $x + y = 2m$ (even).
    - Since $x$ is even, $y = 2m - x$ must also be even.
    - For $y$ (sum of odd numbers) to be even, the *number of odd-degree vertices* must be even.

<br>

- **Example**: In the following graph with 5 vertices:
    - Degrees of each node: {0→2, 1→2, 2→3, 3→3, 4→4}
    - Summation of the degrees of the vertices = $7*2 = 14$
    - Odd-degree vertices: two (3 and 3), which is even.
  
<p align="center">
    <img src="Media\Lecture1\example_graph.png" width="" />
</p>

- Why it matters and it's applications: 
  - **Eulerian Path Detection:** Instantly rule out Eulerian paths/circuits in route planning (e.g., logistics): If ≠0 or 2 odd-degree vertices, no solution exists. (An Eulerian path in a graph is a sequence of edges that visits every edge exactly once.)
  - **Network Anomaly Detection:** In cybersecurity graphs, unexpected odd-degree counts signal data manipulation (e.g., forged transactions in blockchain networks).
  - **Graph Generation:** Validate synthetic graphs in probabilistic models (Erdős–Rényi) before simulation.

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

### Corollary 2.2.3
**Statement**: Every regular graph with an odd degree has an even number of vertices. <br>
- **Proof**:
  - **Handshaking Lemma**: In any graph, the sum of all vertex degrees equals twice the number of edges. This sum is always **even** because it's $2 \times \text{edges}$
  - **Regular graph property**: If a graph is $k$-regular, every vertex has degree $k$. Thus, the sum of degrees is $n \times k$ (where $n = \text{number of vertices}$).
  - **Odd $k$ constraint**: If $k$ is odd, then $n \times k$ must be even (per the handshaking lemma).
  - **Key insight**: An odd number ($k$) multiplied by another number ($n$) only gives an even result if $n$ is **even**. Thus, $n$ must be even when $k$ is odd.
<br>
- **Example**: A 3-regular graph (cubic graph) with an odd degree must have an even number of vertices (e.g., the Petersen graph has 10 vertices).

<p align="center">
    <img src="Media\Lecture1\The-Petersen-graph.png" width="300" /> <br>
    <em>Petersen graph</em>
</p>

- Why it matters and it's pracitcal applicatoins:
  - **Network Design:** Prevent impossible topologies in infrastructure (e.g., 3-regular "cubic" networks like power grids must have *even* nodes).
  - **Error-Correcting Codes:** Guide parity-check matrix construction in LDPC codes, where odd-degree constraints improve error resilience.
  - **Sports Scheduling:** Ensure valid round-robin tournaments where each team plays *k* games (odd *k* requires even teams).


---

### Corollary 2.2.4
**Statement**: A $k$-regular graph with $n$ vertices has $\frac{nk}{2}$ edges. <br>
- **Proof**:
  - **Sum of degrees**: In a $k$-regular graph, the sum of all vertex degrees is $n \times k$ (since each of $n$ vertices has degree $k$).
  - **Handshaking Lemma**: This sum also equals $2 \times \text{edges}$ (denoted $2e$).
  - **Equation**: $n \times k = 2e$.
  - **Solve for edges**: Rearrange to get $e = \frac{n \times k}{2}$.
<br>
- **Example**: A 3-regular graph with 4 vertices has $\frac{4 \times 3}{2} = 6$ edges

<p align="center">
    <img src="Media\Lecture1\example_2.2.4.png" width="" />
</p>

- Why it matters and it's pracitcal applicatoins:
  - **Resource Allocation:** Precompute cloud network costs (e.g., Azure/AWS): *k*-regular graphs minimize connections while ensuring fault tolerance.
  - **Parallel Computing:** Design interconnect topologies (e.g., hypercubes, meshes) where edges = `(n*k)/2` defines communication overhead.
  - **Graph Sampling:** Estimate subgraph properties in large networks (e.g., via *k*-regular random subgraphs).
---

### Subgraphs

- A **subgraph** of graph $G = (V, E)$ is any graph $G' = (V', E')$ where:
    - $V' \subseteq V$ (vertices are a subset of original vertices)
    - $E' \subseteq E$ (edges are a subset of original edges)
- *Example*: Graphs in Figs. 2.6(b)–(e) are subgraphs of Fig. 2.6(a).
- If we delete any number of vertices or edges from a graph, the resulting graph will be a subgraph of the original graph.

<p align="center">
    <img src="Media\Lecture1\subgraph.png" width="" />
</p>

- An **induced subgraph** is a specific type of subgraph that includes all the edges between the selected vertices that are present in the original graph. For example, in the following graph if we select only 0, 2, 3, the induced subgraph will not have the vertex 1 and it's edges. 

<p align="center">
    <img src="Media\Lecture1\example_2.2.4.png" width="300" />
    <img src="Media\Lecture1\induced_subgraph.png" width="250" /> <br>
    <em>The right graph is induced subgraph of the left one for Vertices set ={0, 2, 3}</em>
</p>

### Key Graph Classes

#### 1. Null Graphs

- Graphs with **no edges** (empty edge set). (Notation: $N_n$)
- Every null graph is a subgraph of any graph with the same number of vertices.


#### 2. Complete Graphs
-  Every pair of distinct vertices is **directly connected** by an edge. (Notation: $N_n$)
- **Edge Count** =  $\frac{n(n-1)}{2}$ edges.
- All graphs are subgraphs of $K_n$ with the same vertex count.

<p align="center">
    <img src="Media\Lecture1\null_graph and complete_graph.png" width="" />
</p>

#### 3. Bipartite Graphs

- If vertex set can be split into **two independent sets**/partite sets, the graph is called bipartite graph. Edges **only cross** between the two sets.
  - **Independent Set**: A vertex subset where **no two vertices are adjacent** (no edges between them)
- **Testing Bipartiteness**:
    - Use BFS to **color vertices** with two colors.
    - If **no adjacent vertices share a color** → bipartite 
  
<p align="center">
    <img src="Media\Lecture1\bipartite and non-bipartite.jpg" width="" /><br>
    <em>An example of a bipartite graph and a non-bipartite graph</em>
</p>

- **Complete Bipartite Graph ($K_{m,n}$)**:
    - Every vertex in set $V_1$ connects to every vertex in set $V_2$.
    - **Edge Count** = $m \times n$ (e.g., $K_{3,4}$ has 12 edges.)

<p align="center">
    <img src="Media\Lecture1\K3,4 graph.png" width="200" /> <br>
    <em>K<sub>3,4</sub> complete bipartite graph</em>
</p>

#### 4. Path Graphs

- Vertices arranged in a **linear sequence** with edges only between consecutive vertices. $P_n$ (e.g., $P_6$ has 6 vertices, Fig. 2.9a).
- **Degrees**:
    - End vertices: degree 1.
    - Internal vertices: degree 2.

#### 5. Cycle Graphs

- **Definition**: Path graphs where **first and last vertices are connected** (closed loop).
- **Notation**: $C_n$ (e.g., $C_6$ has 6 vertices, all degree 2, Fig. 2.9b).

#### 6. Wheel Graphs

- **Definition**: A **cycle graph $C_{n-1}$** + a **central vertex $w$** connected to all cycle vertices.
- **Notation**: $W_n$ (e.g., $W_7$ has 6 cycle vertices + 1 central vertex, Fig. 2.9c).
- **Central Vertex Degree**: $n-1$ (connects to all cycle vertices).

<p align="center">
    <img src="Media\Lecture1\path, cycle, wheel graph.png" width="" /> <br>
    <em>Path graph, Cycle graph and Wheel graph</em>
</p>

### Operations on Graphs
Let G₁ = (V₁, E₁) and G₂ = (V₂, E₂) be two graphs.

#### Union of Graphs
(G₁ ∪ G₂) = The resulting graph will contain all the vertices and edges of both graphs.

#### Intersection of Graphs
(G₁ ∩ G₂) = The resulting graph will contain only the vertices and edges that are present in both graphs. <br>


<p align="center">
    <img src="Media\Lecture2\union_and_intersection.png" width="" /> <br>
    <em>Union and Intersection Example</em>
</p>


**Example 1**: Imagine two social networks - Facebook friends and Instagram followers. The union would show all your connections across both platforms, while the intersection would show only people who follow you on both platforms. <br>

<p align="center">
    <img src="Media\Lecture2\union_intersection_example2.png" width="" /> <br>
    <em>Union and Intersection Practical Example</em>
</p>

**Example 2**: Suppose there are h + g people in a party; h of them are hosts and g of them are
guests. Each person shakes hands with each other except that no host shakes hands
with any other host. The problem is to find the total number of handshakes. As usual,
we transform the scenario into a graph problem as follows. We form a graph with
h + g vertices; h of them are black vertices, representing the hosts and the other
g vertices are white, representing the guests. The edges of the graph represent the
handshakes. Thus, there is an edge between every pair of vertices except for that there
is no edge between any pair of black vertices. Thus, the problem now is to count the
number of edges in the graph thus formed. The graph is illustrated for h = 3 and
g = 4 in Fig. 2.11(a). <br>
To solve the problem, we note that the graph can be thought of as a union of two
graphs: a complete graph Kg and a complete bipartite graph Kh,g as illustrated in
Fig. 2.11(b). Since there is no common edge between the two graphs, their intersection contains no edges. Thus, the total number of edges in the graph (i.e., the total
number of handshakes in the party) is n(n − 1)/2 + m × n <br>

#### Complement of Graphs
For a graph h G = (V, E) the complement graph is Ḡ = (V,  Ē) where Ē(G) = E(K<sub>V</sub>) - E(G) 

- A null graph
is the complement of the complete graph with the same number of vertices and vice
versa.

<p align="center">
    <img src="Media\Lecture2\complement_graph.png" width="" /> <br>
</p>

#### Corollary 2.5.1

**Statement:** For any graph G with 6 vertices, either G or Ḡ contains a triangle (3-cycle). (Also called Ramsey's Triangle Theory) <br>

**Proof:**

- Choose any vertex v in the 6-vertex graph G
- v can connect to at most 5 other vertices (since there are 6 vertices total)
- Pigeonhole Principle: v must have at least 3 neighbors in either G or Ḡ
- If v has fewer than 3 neighbors in G, it has at least 3 neighbors in Ḡ
- Case Analysis: Assume v has three neighbors x, y, z in G

    - Case 1: If any two of {x, y, z} are connected in G → triangle found in G

    - Case 2: If no two of {x, y, z} are connected in G → they form a triangle in Ḡ

#### Subdivisions
Subdividing an edge means replacing it with a path of length 2 by adding a new vertex in the middle. <br>

**Example**: If you have a direct road between two cities, subdividing would be like adding a rest stop in the middle - now you have two road segments instead of one direct route.

<p align="center">
    <img src="Media\Lecture2\subdivisions.png" width="" /> <br>
</p>

#### Edge Contraction
Contracting an edge means merging its two endpoints into a single vertex. <br>

**Example**: Think of merging two neighboring cities into one metropolitan area - all roads that led to either city now lead to the merged city.

<p align="center">
    <img src="Media\Lecture2\edge_contraction.png" width="" /> <br>
</p>

### Graph Isomorphism
- Two graphs are **isomorphic** if they have the same structure, even if their vertices have different labels. It's like having two identical puzzles with different colored pieces - the shape and connections are the same. $(G₁ ≅ G₂)$

- Determining if two graphs are isomorphic is surprisingly difficult - no efficient algorithm is known, making it one of computer science's famous unsolved problems.

- Some special graphs look identical to their complement. The 5-vertex cycle (C₅) is an example it has the same structure as its complement. These are called self **complementary graphs**.


<p align="center">
    <img src="Media\Lecture2\isomorphism.png" width="" /> <br>
</p>

### Corollary 2.6.1
**Statement:** The isomorphism relation is an equivalence relation on the set of graphs. <br>

**Proof:** <br>
For any relation to be called an "equivalence relation," it must satisfy three properties <br>

- Reflexive Property Rule: Every graph is isomorphic to itself. <br>
    - Simple explanation: A graph has the same structure as itself (obviously!)

- Symmetric Property Rule: If graph A is isomorphic to graph B, then graph B is isomorphic to graph A.

- Transitive Property Rule: If graph A is isomorphic to graph B, AND graph B is isomorphic to graph C, then graph A is isomorphic to graph C.

<br>

**Why This Matters**
This lemma is important because it means we can group graphs into equivalence classes - collections of graphs that all have the same structure. Within each class, all graphs are isomorphic to each other.
We need to do less caclulations in that case.

### Degree Sequence

- The **degree sequence** lists all vertex degrees in descending order. It's like a summary of how "popular" each vertex is in terms of connections.

<p align="center">
    <img src="Media\Lecture2\degree_seq1.png" width="" /> <br>
    <em>Two degree equivalent graphs<em>
</p>

- **Graphic Sequence**: A sequence of numbers that can actually represent the degrees of vertices in some simple graph.

    - **Example**: The sequence (3,3,2,2,2,0) is graphic because you can draw a graph where two vertices have degree 3, three vertices have degree 2, and one vertex has degree 0.
    The sequence (5, 4, 3, 2, 1, 1) is not graphic sequence.

<p align="center">
    <img src="Media\Lecture2\degree_seq2.png" width="" /> <br>
    <em>Not a graphic sequence<em>
</p>


#### Testing if a sequence is graphic
- Havel and Hakimi showed that d is graphic if and only if d' (complement of d) is graphic.

<p align="center">
    <img src="Media\Lecture2\degree_seq3.png" width="" /> <br>
</p>

The **Havel-Hakimi algorithm** is a method for determining whether a given sequence of non-negative integers can represent the degree sequence of a simple graph (i.e., whether the sequence is "graphic"). <br>

The algorithm works by repeatedly applying a reduction operation to test if a degree sequence is realizable as a simple graph. <br>

**Input**: A sequence of non-negative integers d = (d₁, d₂, ..., dₙ) arranged in non-increasing order. <br>

**Process**: <br>

1. **Base Case**: If the sequence contains only zeros, then it's graphic (represents a null graph)
2. **Reduction Step**:
    - Take the largest degree d₁
    - Remove d₁ from the sequence
    - Subtract 1 from the next d₁ largest degrees in the sequence
    - Rearrange the resulting sequence in non-increasing order
3. **Repeat**: Continue this process until either:
    - You get all zeros (sequence is graphic)
    - You get negative numbers (sequence is not graphic)

**Step-by-Step Example** <br>

Let's test if the sequence (4,4,4,4,3,1) is graphic: <br>

**Step 1**: (4,4,4,4,3,1)

- Remove first 4
- Subtract 1 from next 4 elements: (4-1, 4-1, 4-1, 3-1, 1, 0) = (3,3,3,2,1,0)

**Step 2**: (3,3,3,2,1,0)

- Remove first 3
- Subtract 1 from next 3 elements: (3-1, 3-1, 2-1, 1, 0) = (2,2,1,1,0)

**Step 3**: (2,2,1,1,0)

- Remove first 2
- Subtract 1 from next 2 elements: (2-1, 1-1, 1, 0) = (1,0,1,0)
- Rearrange: (1,1,0,0)

**Step 4**: (1,1,0,0)

- Remove first 1
- Subtract 1 from next 1 element: (1-1, 0, 0) = (0,0,0)

**Result**: All zeros → The sequence is **graphic**


<p align="center">
    <img src="Media\Lecture2\degree_seq4.png" width="" /> <br>
</p>

### Graph Representation
To be Added

# Chapter 3

<p align="center">
<img src="Media\Lecture1\multi_graph.png" width="" /> <br/>
    <em>A multigraph example</em>
</p>

<p align="center">
<img src="Media\Lecture3\chapt3_first_image.png" width="" /> <br>
    <em>A simple graph example</em>
<p align="center">

### Walks
A walk is a sequence of alternating vertices and edges where each edge connects consecutive vertices. It can repeat both vertices and edges. <br>
For example: <br>
In the multigraph example, v1, e1, v5, e5, v5, e5, v5, e8, v3; is a walk <br>
In the simple graph example, a, (a,i), i, (i, h), h, (h, c), c, (c, b), b, (b, a), a; is a walk

### Trails
A trail is a walk in a graph where no edge is repeated, but vertices can be repeated.
<br>
For example: <br>
In the multigraph example, v1, e1, v5, e5, v5, e8, v3, e7, v2, e6, v3; is a trail. <br>
In the simple graph example, a, (a,i), i, (i, h), h, (h, c), c, (c, b), b, (b, a), a; is a trail.

> A closed trail that starts and ends at the same vertex, with no repeated edges is called a **circuit**.

### Paths
A path is a walk with no repeated vertices.
<br>
For example: <br>
In the multigraph example, v1, e1, v5, e8, v3, e7, v2; is a path. <br>
In the simple graph example, a, (a,i), i, (i, h), h, (h, c), c, (c, b), b, (b, a), a; is a path.

### Cycles
A Cycle is a path except start and end vertex is same.
<br>
For example: <br>
In the multigraph example, v1, e1, v5, e8, v3, e7, v2, e3, v1; is a cycle. <br>
In the simple graph example, a, (a,i), i, (i, h), h, (h, c), c, (c, b), b, (b, a), a; is a cycle.

#### Lemma 3.1.1 
**Statement:** Every u,v-walk contains a u,v-path <br>
- Meaning that, if you walk from u to v even with a lot of cycles in between u and v, there's always a direct path from u to v without any detours.

**Proof:** <br>
- If the walk has no repeated vertices → it's already a path.
- If the walk has repeated vertices → remove the "loop" between repeated occurrences. This creates a shorter walk that still connects u to v.

### Graph Connectivity/Connected Components
- Connected Graph: You can travel between any two vertices
- Disconnected Graph: Some vertices are unreachable from others

<p align="center">
<img src="Media\Lecture1\graph_connectivity.png" width="" />
<p align="center">

#### Lemma 3.1.2
**Statement:** Every graph with n vertices and m edges has at least n − m connected component. <br.>
- Basically ``Components ≥ n - m``
**Proof:** <br>
- Base case: A graph with n vertices and 0 edges has n components (each vertex is isolated)
- Each time we add an edge, we can decrease the number of components by at most 1. (Either the edge connects two components into one or the edge connects two vertices in the same component)
- So, After adding m edges: components ≥ n - m

#### Lemma 3.1.3
**Statement:** Let G be a simple graph of n vertices. If G has exactly k components, then the number m of edges of G satisfies <br>
$n − k ≤ m ≤ (n − k)(n − k + 1)/2$ <br>

**Lower Bound Proof (n - k ≤ m):** <br>
- If we remove any edge from a graph with minimum edges, components must increase.

**Upper Bound Proof (m ≤ (n-k)(n-k+1)/2):**
- To maximize edges with k components, make one component as large as possible
- Optimal configuration: one complete graph with (n-k+1) vertices + (k-1) isolated vertices
- Maximum edges = (n-k)(n-k+1)/2   {We know these from complete graph}

### Cut-Edges
An edge is a cut edge if removing it disconnects the component. Removing cut-edges increases the number of components.

#### Lemma 3.1.4
**Statement:**  An edge is a cut-edge if and only if it belongs to no cycle.<br>

- Think of this like bridges in a city. A bridge is critical (a cut-edge) only if there's no alternative route around it.

**Proof:**
- If we remove edge (x,y) and vertices x and y are still connected
- There must be an alternative path P from x to y
- This path P + the original edge (x,y) forms a cycle



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