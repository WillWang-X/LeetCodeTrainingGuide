<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Breadth-first_search">
  <img src="https://i.imgur.com/c0F4gTc.gif" alt="BFS" width=42%">
  </a>
  <br><br>
BFS
  <br><br>
</h1>

> Breadth-first search (BFS) is an algorithm for traversing or searching tree or graph data structures. It starts at the tree root (or some arbitrary node of a graph, sometimes referred to as a 'search key'), and explores all of the neighbor nodes at the present depth prior to moving on to the nodes at the next depth level. [[wiki](https://www.wikiwand.com/en/Breadth-first_search)]

## 📝1. Basics

* BFS visit nodes level by **level** in Graph.
* A node is fully explored before any other can begin.
* Uses **Queue** data structure to store Un-explored nodes.
* BFS is slower and require more **memory**.

Some Application:

* Finding all **connected components** in a graph.
* Finding the **shortest** path between two nodes.
* Finding all nodes within **one** connected component.
* Testing a graph for **bipartiteness**.

## ⚔️2. Use cases

1. Traversal: 133, 301
2. Connected Components: 200, 261, 323
3. Shortest Path: 🌟[126 word ladder], 127,286, 317, [542. 01 Matrix](https://leetcode.com/problems/01-matrix/)
4. Topological: [207](https://leetcode.com/problems/course-schedule/), [269](https://leetcode.com/problems/alien-dictionary/) 

## 🤺3. Best Practices

- traverse layer by layer(depth)
- connected component 
- path
- shortest distance

#### traverse layer by layer 

``` python
front = [start]
depth = 0
while front:
	nxt = []
	for node in front:
		for child in children(node):
			nxt.append(child)
	front = nxt 
	depth += 1	
```

``` python
seen, targets = set(), set()
queue = [(node, 1) for node in seen]
for node, depth in queue:
    if node in targets: return depth
    for nei in graph[node]:
        if nei not in seen:
            seen.add(nei)
            queue.append((nei, depth+1))
```

- Try [815](https://leetcode.com/problems/bus-routes/)

#### connected component 

``` python
graph = {'A': set(['B', 'C']),
         'B': set(['A', 'D', 'E']),
         'C': set(['A', 'F']),
         'D': set(['B']),
         'E': set(['B', 'F']),
         'F': set(['C', 'E'])}
``` 

``` python 
def bfs(graph, start):
    visited, queue = set(), [start]
    while queue:
        vertex = queue.pop(0)
        if vertex not in visited:
            visited.add(vertex)
            queue.extend(graph[vertex] - visited)
    return visited

bfs(graph, 'A') # {'B', 'C', 'A', 'F', 'D', 'E'}
```

#### path

``` python 
def bfs_paths(graph, start, goal):
    queue = [(start, [start])]
    while queue:
        vertex, path = queue.pop(0)
        for nxt in graph[vertex] - set(path):
            if nxt == goal:
                yield path + [nxt]
            else:
                queue.append((nxt, path + [nxt]))

list(bfs_paths(graph, 'A', 'F')) # [['A', 'C', 'F'], ['A', 'B', 'E', 'F']]
```

``` python
def shortest_path(graph, start, goal):
    try:
        return next(bfs_paths(graph, start, goal))
    except StopIteration:
        return None

shortest_path(graph, 'A', 'F') # ['A', 'C', 'F']
```

#### shortest distance

``` python
# bfs: 1. pop 2. check 3. add unseen neighbors
def neighbor(node):
	return graph[node]

def shortest_depth(graph, start, goal):
	seen, queue = set([start]), [(start, 0)]
	while queue:
		node, depth = queue.pop(0) # deque
		# base case 
		if node == goal: return depth 
		# general case 
		for nxt in neighbor[node] - seen:
			queue.append((nxt, depth+1))
			seen.add(nxt)
	return -1	
```

## 😈4. More training

1. 301 Remove Invalid Parentheses 
1. 133 Clone Graph  ❶ 
1. 323 Number of Connected Components in an Undirected Graph
1. 200 Number of Islands
1. 261 Graph Valid Tree ❷
1. 127 Word Ladder 
1. 286 Walls and Gates 
1. 317 Shortest Distance from All Buildings  ❸
1. 207 Course Schedule 
1. 269 Alien Dictionary 
1. [444 Sequence Reconstruction](https://leetcode.com/problems/sequence-reconstruction/) ❹
2. [631. Design Excel Sum Formula](https://leetcode.com/problems/design-excel-sum-formula/)
2. [815. Bus Routes](https://leetcode.com/problems/bus-routes/)

## 💬5. Explanation

## ⚠️6. FAQs

#### Q: BFS cs Dijsktra?

A: Edge == 1, Dijsktra 退化成 BFS。因为如果每一条权值相同，即无权图，那么从源(Source)开始访问图(Graph)遇到节点的最小深度就等于到该节点的最短路径，因此Priority Queue就退化成了Queue, `Dijkstra`算法就退化成了BFS。

- [787. Cheapest Flights Within K Stops
](https://leetcode.com/problems/cheapest-flights-within-k-stops/): BFS is not a good choice
- [847. Shortest Path Visiting All Nodes](https://leetcode.com/problems/shortest-path-visiting-all-nodes/): use BFS instead Dijkstra

