# [98](https://leetcode.com/problems/validate-binary-search-tree/). Validate Binary Search Tree

## 1. Problem

Given a binary tree, determine if it is a valid binary search tree (BST).


``` python
# Binary Tree -> Valid BST?
# TreeNode    -> Boolean
I:
    2
   / \
  1   3
O: true
```

Clarification:

* **BST**: The left subtree of a node contains only nodes with keys **less than** the node's key. The right subtree of a node contains only nodes with keys **greater than** the node's key. Both the left and right subtrees must also be binary search trees.

## 2. Ideas

### BF: iterate

Each node in BST has its upper and lower limits. 

* One compares the node value with its upper and lower limits if they are available. 
* Compare root of the current subtree with these two values. Then, recursively check the left and right subtree of the current one. Take care of the values passed down.

### BF: compare by inorder

The property of BST is that order of inorder traversal means for BST that each element should be smaller than the next one.


## 3. Example

The node `x`: its upper limits is `10` and its lower limits is `6`.

``` 
      6 
    /   \
  4      10
        /
       x
```


## 4. Code 

``` python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
```


### v0.1 defintion 

``` python
class Solution:
    def isValidBST(self, root: TreeNode) -> bool:
        return self.is_valid_BST_rec(root)
    
    def is_valid_BST_rec(self, root, low = float("-inf"), high = float("inf")):
        if not root: return True 
    
        if root.val <= low or root.val >= high:
            return False 
        
        return  self.is_valid_BST_rec(root.left, low, root.val) and \
                self.is_valid_BST_rec(root.right, root.val, high)
```

### v0.2 inorder(recursive) + definition 

``` python 
# not efficient but intuitive
def isValidBST(self, root):
    """
    :type root: TreeNode
    :rtype: bool
    """
    result = []
    
    def inorder(root, result) :
        if root :
            inorder(root.left, result)
            result.append(root.val)
            inorder(root.right, result)
            
    inorder(root, result)
    return sorted(list(set(result))) == result

```

### v0.3 inoder(iterative) + early stop instead of creating a new list 

``` python
# Time: O(n) where n = the number of node

class Solution:
    def isValidBST(self, root: TreeNode) -> bool:
        stack, inorder = [], float("-inf")
        
        while stack or root:
            while root:
                stack.append(root)
                root = root.left 
            
            root = stack.pop() # pop instead of write 
            if root.val <= inorder:
                return False 
            inorder = root.val
            
            root = root.right
            
        return True 
```

## 5. Test 

```
[2,1,3]
```