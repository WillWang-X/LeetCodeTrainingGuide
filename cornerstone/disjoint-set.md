<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Disjoint-set_data_structure">
  <img src="https://camo.githubusercontent.com/c885a811800fc105c74f5584aacaecfb1305e327/68747470733a2f2f692e696d6775722e636f6d2f4f6c64556661312e6a7067" alt="Disjoint-set" width=42%">
  </a>
  <br><br>
Disjoint-set 
  <br><br>
</h1>

> In computer science, a disjoint-set data structure, also called a union–find data structure or merge–find set, is a data structure that stores a **collection of disjoint** (non-overlapping) sets. [[wiki](https://www.wikiwand.com/en/Disjoint-set_data_structure)]

## 📝1. Basics

In computer science, a disjoint-set data structure, also called a union–find data structure or merge–find set, is a data structure that stores a collection of disjoint (non-overlapping) sets. Equivalently, it stores a **partition** of a set into disjoint subsets. 

 It provides operations for **adding** new sets, **merging** sets (replacing them by their union), and finding a **representative** member of a set. The last operation allows to find out **efficiently** if any two elements are in the **same** or different sets.


## ⚔️2. Use cases

* Find component (in **dynamic graph**): [305](https://leetcode.com/problems/number-of-islands-ii/)
* Detect cycle for the whole graph
* MST(Kruskal)

## 🤺3. Best Practices

``` python
# https://repl.it/@WillWang42/union-find

class Union(object):

  def __init__(self):
    self.id = {}
    self.sz = {}    
    self.count = 0
  
  def add(self, x):
    self.id[x] = x
    self.sz[x] = 1
    self.count += 1 

  def root(self, x):
    if self.id[x] == x:
      return x 
    return self.root(self.id[x])
       
  def unite(self, x, y):
    i = self.root(x)
    j = self.root(y)
    if i == j: return 

    if self.sz[i] > self.sz[j]:
      i, j = j, i
    self.id[i] = j
    self.sz[j] += self.sz[i]
    self.count -= 1
```  

## 😈4. More training

* 323 Number of Connected Components in an Undirected 
* [305. Number of Islands II](https://leetcode.com/problems/number-of-islands-ii/)

## 💬5. Explanation 

## ⚠️6. FAQs 

#### Q: Union-Find or DFS: which one is better to find connected component?

A: 

> tl;dr - Static graph? DFS! Dynamic graph? Union-find!

The union-find algorithm is best suited for situations where the equivalence relationship is changing, i.e., there are "Union" operations which need to be performed on your set of partitions. Given a fixed undirected graph, you don't have the equivalence relationships changing at all - the edges are all fixed. OTOH, if you have a graph with new edges being added, DFS won't cut it. While DFS is asymptotically faster than union-find, in practice, the likely deciding factor would be the actual problem that you are trying to solve.

source: [stackoverflow](https://stackoverflow.com/questions/28398101/union-find-or-dfs-which-one-is-better-to-find-connected-component)


#### Q: recursion vs iteration for the function `root()`?

A: Itreation may be better for large data considering the overhead of repeated function calls for recursion, Although recursion is advantageous in shorter code.

#### Q: {} or [] for initialization?

A: union find is better than DFS for dynamic graph. Thus, {} is a better choice. 


#### Q: Why is the size better than the depth for union operation?

A: It is faster for most of nodes to find its parent.