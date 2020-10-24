<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Binary_tree">
  <img src="https://i.imgur.com/OtqGoIa.png" alt="Binary Tree" width=42%">
  </a>
  <br><br>
Binary Tree
  <br><br>
</h1>

> A tree whose elements have at most 2 children. [[wiki](https://www.wikiwand.com/en/Binary_tree)]

## 📝1. Basics

 **Recursive algorithms** are well-suited to problems on trees. Remember to include space implicitly allocated on the **function call stack** when doing space complexity analysis. 
 
Some tree problems have simple brute-force solutions that use 0(n) space solution, but subtler solutions that uses the **existing tree nodes** to reduce space complexity to 0( 1). 

Consider **left- and right-skewed trees** when doing complexity analysis. Note that 0(h) complexity, where h is the tree height, translates into 0(log n) complexity for balanced trees, but 0(n) complexity for skewed trees. 

If each node has a **parent field**, use it to make your code simpler, and to reduce time and space complexity. 

It's easy to make the **mistake** of treating a node that has a single child as a leaf. 

## ⚔️2. Use cases


* [Operation](https://www.wikiwand.com/en/Tree_(data_structure)#/Common_operations): merge, trim, invert, flatten, insert, flip, recover, construct, convert
* [Attribute](https://www.wikiwand.com/en/Tree_(data_structure)#/Terminology): unique, univalued, depth, view, leaves, average, print, width, tilt, diameter, boundary, path, ancestor, closest value, closet leaf
* Path: path sum

## 🤺3. Best Practices

 
- search
	- **recursive** 
	- iterative
- calculate
	- pass info to children (target)
	- get info from children (sum) 
	- path sum
- modify 


### recursive (merge)

``` python
def merge_trees(self, t1: TreeNode, t2: TreeNode) -> TreeNode:
	# Base Case 
    if not t1: return t2
    if not t2: return t1
    # Do sth.
    t1.val += t2.val
    # General Case
    t1.left  = self.merge_trees(t1.left, t2.left)
    t1.right = self.merge_trees(t1.right, t2.right)
    return t1
```

### iterative (view)

``` python
def right_side_view(self, root: TreeNode) -> List[int]:
    if not root: return []
    front = [root]
    sight = []
    while front:
        sight.append(front[-1].val)

        nxt = []
        for node in front: 
            if node.left:  nxt.append(node.left)
            if node.right: nxt.append(node.right)
        front = nxt 

    return sight 

```
### pass info to children, e.g. 算了再说 `target -= node.val` 

``` python
def max_ancestor_diff(self, node, high, low):
	# Base Case 
    if not node:
        return high - low
    # Do sth.
    high = max(high, node.val)
    low  = min(low,  node.val)
    # General Case 
    return max(max_ancestor_diff(node.left,  high, low), \
               max_ancestor_diff(node.right, high, low))
```

### get info from children, e.g. 最后再算`sum(path)`

``` python
def min_depth(self, root: TreeNode) -> int:
	# Edge Case 
    if not root: return 0
        
    # Base Case 
    children = [root.left, root.right]
    if not any(children): return 1
	
	# General Case 
    min_ = float('inf')
    for c in children:
        if c:  min_ = min(min_depth(c), min_)
        
    return min_ + 1
```

## 😈4. More training

* [112. Path Sum](https://leetcode.com/problems/path-sum/)
* [113. Path Sum II](https://leetcode.com/problems/path-sum-ii/)
* [124. Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)
* [437. Path Sum III](https://leetcode.com/problems/path-sum-iii/)
* [666. Path Sum IV](https://leetcode.com/problems/path-sum-iv/)

## 💬5. Explanation

## ⚠️6. FAQs

#### Q: What are corner cases for binary tree problems?

A: Here are 4 I think of: 

* root == `None`
* negative value 
* empty tree\ single node \ two nodes
* Very skewed tree (like a linked list).

