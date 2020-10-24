<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Binary_search_tree">
  <img src="https://i.imgur.com/oAQtYTl.gif" alt="binary search tree" width=42%">
  </a>
  <br><br>
Binary Search Tree
  <br><br>
</h1>

> In computer science, a binary search tree (BST), also called an ordered or sorted binary tree, is a rooted binary tree whose internal nodes each store a key **greater than** all the keys in the node's left subtree and **less than** those in its right subtree. [[wiki](https://www.wikiwand.com/en/Binary_search_tree)]

## 📝1. Basics

With a BST you can **iterate** through elements in **sorted order** in time O(n) (regardless of whether it is balanced).

Some problems need a combination of **a BST and a hashtable**. For example, if you insert student objects into a BST and entries are ordered by GPA, and then a student’s GPA needs to be updated and all we have is the student’s name and new GPA, we cannot find the student by name without a full traversal. However, with an additional hash table, we can directly go to the corresponding entry in the tree.

The BST property is a **global property**—a binary tree may have the property that each node’s key is greater than the key at its left child and smaller than the key at its right child, but it may not be a BST.

### lists of fact 

- Inorder traversal of BST is an array sorted in the ascending order
- To compute inorder traversal follow the direction `Left -> Node -> Right`.
- **Successor** = "after node", i.e. the next node, or the smallest node after the current one.
- **Predecessor** = "before node", i.e. the previous node, or the largest node before the current one.


## ⚔️2. Use cases

- isBST
	- successor
	- predecessor
- sorted
	- inorder generator, [1038](https://leetcode.com/problems/binary-search-tree-to-greater-sum-tree/)
	- inorder traverse (iterative / recursive)
	- inorder array
- search (logn)
	- kth
	- delete 
 

## 🤺3. Best Practices

- isBST
- to ordered array
- inorder generator
- successor 
- predecessor
- kth smalllest (iterative)
- delete a node in BST? 


#### isBST

``` python
def is_valid_BST(root, lower = float("-inf"), upper = float("inf")):
    if not root: 
    	return True 
    
    if root.val <= lower or root.val >= upper:
        return False 
    
    return  is_valid_BST(root.left,  lower, root.val) and \
            is_valid_BST(root.right, root.val, upper)
```

#### inorder

> BST to a array ordered in the the ascending order

To compute inorder traversal follow the direction Left -> Node -> Right.


``` python
def inorder(root):
    return inorder(root.left) + [root.val] + inorder(root.right) if root else []

def helper(self, ans, root):
    if root is None: return ans 
    ans.append(root.val)
    return self.helper([], root.left) + ans + self.helper([], root.right)   
   
def inorder_generator(self, root):
    if root:
        for val in self.inorder(root.left):  yield val
        yield root.val
        for val in self.inorder(root.right): yield val    

def inorder_iterative(root):
	stack = []
	while stack or root:
		while root:
			stack.append(root)
			root.left 
		node = stack.pop()
		# do sth. with node 
		root = node.right   

# general way 
def inorder_traversal(root: TreeNode) -> List[int]:
    stack = [(0, root)]
    ans = []
    while stack:
        opt, node = stack.pop()
        if node is None: continue 
        if opt == 0:
            stack.append((0, node.right))
            stack.append((1, node))
            stack.append((0, node.left))
        else:
            ans.append(node.val)
    return ans
```

#### sucessor

> Successor = "after node", i.e. the next node, or the smallest node after the current one.

It's also the next node in the inorder traversal. To find a successor, go to the right once and then as many times to the left as you could.




``` python
def successor(root):
    root = root.right
    while root.left:
        root = root.left
    return root
```

#### predecessor

> Predecessor = "before node", i.e. the previous node, or the largest node before the current one.  

To find a predecessor, go to the left once and then as many times to the right as you could.

``` python
def predecessor(root):
    root = root.left
    while root.right:
        root = root.right
    return root
```


#### kth smallest (iterative+inorder)

``` python
def kth_smallest(root: TreeNode, k: int) -> int:
    stack = []
    while root or stack:
        while root:
            stack.append(root)
            root = root.left
        node = stack.pop()

        k -= 1
        if k == 0:
            return node.val

        root = node.right 
``` 

#### smallest node 

``` python
# smallest node in a sub BST
def _smallest(self, node):
    while node.left:
        node = node.left 
    return node.val
```


#### delete the node 

``` python
def delete_node(root: TreeNode, key: int) -> TreeNode:
    if not root:
        return root
    
    if root.val < key:
        root.right = self.deleteNode(root.right, key)
    elif root.val > key:
        root.left = self.deleteNode(root.left, key)
    else: # == key
        if not root.left:  return root.right
        if not root.right: return root.left 
        # decrease and conquer
        root.val = self._smallest(root.right)  
        root.right = self.deleteNode(root.right, root.val)
        
    return root 
```

## 😈4. More training

- [230. Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)
- [538. Convert BST to Greater Tree](https://leetcode.com/problems/convert-bst-to-greater-tree/)

## 💬5. Explanation

## ⚠️6. FAQs

#### Q: Advantages of BST over Hash Table?

A: Hash Table supports following operations in Θ(1) time.
1) Search
2) Insert
3) Delete

The time complexity of above operations in a self-balancing Binary Search Tree (BST) (like Red-Black Tree, AVL Tree, Splay Tree, etc) is O(Logn).

So Hash Table seems to beating BST in all common operations. When should we prefer BST over Hash Tables, what are advantages. 

Following are some important points in favor of BSTs.

* We can get all keys in **sorted order** by just doing Inorder Traversal of BST. This is not a natural operation in Hash Tables and requires extra efforts.
* Doing order **statistics, finding closest lower and greater elements, doing range queries** are easy to do with BSTs. Like sorting, these operations are not a natural operation with Hash Tables.
* BSTs are **easy to implement** compared to hashing, we can easily implement our own customized BST. To implement Hashing, we generally rely on libraries provided by programming languages.
* With **Self-Balancing BSTs, all operations are guaranteed to work in O(Logn) time.** But with Hashing, Θ(1) is average time and some particular operations may be costly, especially when **table resizing** happens.

source:  [Advantages of BST over Hash Table](https://www.geeksforgeeks.org/advantages-of-bst-over-hash-table/)