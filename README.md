# PyPy3 Algorithmic Architecture & Optimization Suite

This repository is the culmination of my work solving 800+ advanced algorithmic challenges across Codeforces, CSES, and CodeChef. It contains over 30,000 lines of highly optimized data structures, graph algorithms, and combinatorial mathematics. 

The primary objective of this codebase is constraint optimization: enabling Python to successfully execute within the strict 1.0-second time limits typically dominated by C++.

## ⚡ Architecture & Trade-Offs

Standard software engineering prioritizes abstraction, readability, and object-oriented design. This repository deliberately discards those principles in favor of raw execution speed. 

To bridge the performance gap between Python and C++, I have architected these implementations specifically around the behavior of the **PyPy3 Just-In-Time (JIT) compiler**. Achieving acceptable latency in Python requires aggressively minimizing memory allocation and interpreter overhead.

The codebase strictly adheres to the following design constraints:

* **Procedural Flattening:** Python's function call overhead and strict recursion limits are significant bottlenecks. I bypass this by flattening complex tree traversals and dynamic programming states into raw, iterative loops.
* **1D Array Memory Management:** Instantiating objects for tree nodes (e.g., in Segment or Fenwick Trees) causes heap fragmentation and slows down garbage collection. All advanced structures here are flattened into pre-allocated 1D arrays.
* **Syntax Compression:** Variable names and logic flows are mathematically compressed. This is an adaptation for live, high-stakes competitive programming, minimizing typing latency and maximizing rapid deployment. 

## 📂 Implementation Index

This suite maps out thousands of problem states and execution variations. 

### 1. Graph Theory & Network Flow
* Breadth-First and Depth-First Search (Strictly Iterative variants).
* Shortest Paths: Dijkstra (optimized via 1D Min-Heaps), Bellman-Ford, Floyd-Warshall.
* Minimum Spanning Trees: Kruskal's (with DSU) and Prim's.
* Advanced Tree Traversals: Euler Tours, Lowest Common Ancestor (Binary Lifting).

### 2. Range Queries & Trees
* **Segment Trees:** Iterative and Recursive implementations, including Lazy Propagation. 
* **Fenwick Trees (BIT):** Optimized for high-speed dynamic prefix sums.
* **Disjoint Set Union (DSU):** Featuring path compression and union by rank.

### 3. Dynamic Programming & Combinatorics
* State-space reductions (Optimizing $\mathcal{O}(N^2)$ transitions to $\mathcal{O}(N \log N)$).
* Divide & Conquer DP, Convex Hull Trick, and Knuth's Optimization.
* Combinatorial precomputation and modulo arithmetic caching.

## 🚀 Execution

This library is tightly coupled to PyPy3. Executing these scripts in standard CPython will result in suboptimal performance, as CPython lacks the JIT compilation required to aggressively optimize flat procedural loops.

```bash
pypy3 algorithm_file.py < input.txt
