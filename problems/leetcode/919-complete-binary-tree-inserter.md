# [919](https://leetcode.com/problems/complete-binary-tree-inserter/). Complete Binary Tree Inserter



## 1. Problem 

Write a data structure `CBTInserter` that is initialized with a complete binary tree and supports the following operations:

* `CBTInserter(TreeNode root)` initializes the data structure on a given tree with head node root;
* `CBTInserter.insert(int v)` will insert a `TreeNode` into the tree with value `node.val = v` so that the tree remains complete, and returns the value of the parent of the inserted `TreeNode`;
* `CBTInserter.get_root()` will return the head node of the tree.

``` python
# operations -> init/insert & return/return head node
# int/       -> int/TreeNode
I: inputs = ["CBTInserter","insert","get_root"], inputs = [[[1]],[2],[]]
O: [null,1,[1,2]]
```

Clarification: 

* A **complete binary tree** is a binary tree in which every level, except possibly the last, is **completely** **filled**, and all nodes are as far **left** as possible.
* The initial given tree is complete and contains between 1 and 1000 nodes.
* CBTInserter.insert is called at most 10000 times per test case.
* Every value of a given or inserted node is between 0 and 5000.

## 2. Ideas

### BF - BFS

* Collect all nodes that not are not completed filled by BFS
* Insert to the first node in the `unfilled_list` and delete the parent if it is completed filled

## 3. Example

``` python
    2
   / \
   2  4
  /
  5

self.unfilled = [2, 4, 5]
```

## 4. Code 

### v0.2

``` python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class CBTInserter:

    def __init__(self, root: TreeNode):
        self.unfilled = self._bfs(root)
        self.root = root

    def insert(self, v: int) -> int:
        node = self.unfilled[0]
        self.unfilled.append(TreeNode(v))
        if not node.left:
            node.left = self.unfilled[-1]
        else:
            node.right = self.unfilled[-1]
            self.unfilled.popleft()
        return node.val

    def get_root(self) -> TreeNode:
        return self.root

    def _bfs(self, root: TreeNode):
        q = collections.deque([root])
        unfilled = collections.deque()
        while q:
            node = q.popleft()
            if not node.left or not node.right:
                unfilled.append(node)
            if node.left:
                q.append(node.left)
            if node.right:
                q.append(node.right)
        return unfilled

# Your CBTInserter object will be instantiated and called as such:
# obj = CBTInserter(root)
# param_1 = obj.insert(v)
# param_2 = obj.get_root()
```

## 5. Test

```
["CBTInserter","insert","get_root"]
[[[1]],[2],[]]
```