<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Breadth-first_search">
  <img src="https://i.imgur.com/MovXsJO.png" alt="example" width=42%">
  </a>
  <br><br>
Breadth-first search 
  <br><br>
</h1>

> Breadth-first search (BFS) is an algorithm for traversing or searching tree or graph data structures. It starts at the tree root (or some arbitrary node of a graph, sometimes referred to as a '**search key**'), and explores all of the neighbor nodes at the present depth prior to moving on to the nodes at the next depth level. [[wiki](https://www.wikiwand.com/en/Breadth-first_search)]

## Why 

Breadth-first search can be used to solve many problems in **graph theory**, for example:

* Copying **garbage collection**, Cheney's algorithm
* Finding **the shortest path** between two nodes u and v, with path length measured by number of edges (an advantage over depth-first search)[12]
* (Reverse) Cuthill–McKee mesh numbering
* Ford–Fulkerson method for computing the **maximum flow** in a flow network
* **Serialization/Deserialization** of a binary tree vs serialization in sorted order, allows the tree to be **re-constructed** in an efficient manner.
* Construction of the failure function of the Aho-Corasick pattern matcher.
* Testing **bipartiteness** of a graph.

## How

* [learn-anything: breadth-first-search](https://learn-anything.xyz/computer-science/algorithms/search/breadth-first-search)

### Pseudocode

* **Input**: A graph `G` and a starting vertex root of `G`
* **Output**: **Goal state**. The parent links trace the shortest path back to root

``` python
 1  procedure BFS(G, root) is
 2      let Q be a queue
 3      label root as discovered
 4      Q.enqueue(root)
 5      while Q is not empty do
 6          v := Q.dequeue()
 7          if v is the goal then
 8              return v
 9          for all edges from v to w in G.adjacentEdges(v) do
10              if w is not labeled as discovered then
11                  label w as discovered
12                  Q.enqueue(w)
```

This non-recursive implementation is similar to the non-recursive implementation of **depth-first search**, but differs from it in two ways:

* it uses a **queue** (First In First Out) instead of a **stack** and
* it checks whether a vertex has been discovered **before** enqueueing the vertex rather than **delaying** this check until the vertex is dequeued from the queue.

If `G` is a tree, replacing the **queue** of this breadth-first search algorithm with a **stack** will yield a depth-first search algorithm. For general graphs, replacing the stack of the **iterative** depth-first search implementation with a queue would also produce a breadth-first search algorithm, although a somewhat nonstandard one.

The `Q` queue contains the **frontier** along which the algorithm is currently searching.

Nodes can be labelled as discovered by storing them in a set, or **by an attribute** on each node, depending on the implementation.

Note that the word node is usually interchangeable with the word vertex.

The parent attribute of each node is useful for accessing the nodes in **a shortest path**, for example by backtracking from the destination node up to the starting node, once the BFS has been run, and the predecessors nodes have been set.

Breadth-first search produces a so-called **breadth first tree**. You can see how a breadth first tree looks in the following example.

* an example of the [breadth-first tree](https://i.imgur.com/K1mFQqx.png) obtained by running a BFS on German cities starting from Frankfurt.



## What 

### Overview

Breadth-first search (BFS) is an algorithm for **traversing** or searching tree or graph data structures. It starts at the **tree root** (or some arbitrary node of a graph, sometimes referred to as a 'search key'[1]), and explores **all of the neighbor nodes** at the **present** depth **prior to** moving on to the nodes at the **next** depth level.

### History

BFS and its application in finding **connected components** of graphs were invented in 1945 by Konrad Zuse, in his (rejected) Ph.D. thesis on the Plankalkül programming language, but this was not published until 1972.[3] It was reinvented in 1959 by Edward F. Moore, who used it to find the shortest path out of a maze,[4][5] and later developed by C. Y. Lee into a wire routing algorithm (published 1961).[6]

### Others

* Pseudocode
* Analysis
* BFS ordering
* Applications


## FAQs

#### Q: BFS vs DFS?

A: BFS uses the opposite strategy of depth-first search, which instead explores the node branch as **far** as possible before being **forced** to backtrack and **expand** other nodes.



