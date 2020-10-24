<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Graph_traversal">
  <img src="https://i.imgur.com/ArTcbU2.png" alt="graph" width=42%">
  </a>
  <br><br>
Graph
  <br><br>
</h1>

> A graph data structure consists of a finite (and possibly mutable) set of **vertices** (also called nodes or points), together with a set of unordered **pairs** of these vertices for an undirected graph or a set of ordered pairs for a directed graph. [[wiki](https://www.wikiwand.com/en/Graph_(abstract_data_type))]

## 📝1. Basics

source: elements

It’s natural to use a graph when the problem involves **spatially connected** objects, e.g., road segments between cities.

**More generally**, consider using a graph when you need to analyze **any binary relationship**, between objects, such as interlinked webpages, followers in a social graph, etc. In such cases, quite often the problem can be reduced to a well-known graph problem.

Some graph problems entail **analyzing structure**, e.g., looking for cycles or connected compo- nents. DFS works particularly well for these applications.

Some graph problems are related to **optimization**, e.g., find the shortest path from one vertex to another. **BFS, Dijkstra’s shortest path algorithm, and minimum spanning tree** are examples of graph algorithms appropriate for optimization problems.

## ⚔️2. Use cases

## 🤺3. Best Practices

### representation 

* adjacency list (effective with **sparse** graphs)
* adjacency matrix (effective with **dense** graphs)
* [Incidence matrix](https://www.wikiwand.com/en/Incidence_matrix)

``` python 
# adjacency list 
graph = {'A': set(['B', 'C']),
         'B': set(['A', 'D', 'E']),
         'C': set(['A', 'F']),
         'D': set(['B']),
         'E': set(['B', 'F']),
         'F': set(['C', 'E'])}
```

``` python
# adjacency matrix
matrix = [
[1,1,1]
[1,1,1]
[1,1,1]
]
```


## 😈4. More training

## 💬5. Explanation

## ⚠️6. FAQs