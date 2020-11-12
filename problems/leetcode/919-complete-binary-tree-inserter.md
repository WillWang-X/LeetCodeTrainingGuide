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

### [algorithm design paradigm](https://www.wikiwand.com/en/Algorithmic_paradigm) 

concise description about your idea

## 3. Example

dry run of your idea

## 4. Code 

### v0.1

``` python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class CBTInserter:

    def __init__(self, root: TreeNode):
        self.root = root 
        front = [root]
        self.cur = []
        self.p = 0 
        while front:
            nxt = []
            for node in front:
                if not node.left or not node.right:
                    self.cur.append(node)
                if node.left:
                    nxt.append(node.left)
                if node.right:
                    nxt.append(node.right)
            front = nxt 

    def insert(self, v: int) -> int:
        nxt = TreeNode(v)
        cur = self.cur[self.p]
        if not cur.left:
            cur.left = nxt
        else:
            cur.right = nxt
            self.p += 1
        self.cur.append(nxt)
        return cur.val

    def get_root(self) -> TreeNode:
        return self.root         
        

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