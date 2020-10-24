<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Tree_(data_structure)">
  <img src="https://i.imgur.com/wGw8nVy.png" alt="tree" width=42%">
  </a>
  <br><br>
Tree
  <br><br>
</h1>

> A tree is an undirected and connected acyclic graph. [[wiki](https://www.wikiwand.com/en/Tree_(data_structure))]

## 📝1. Basics

A tree data structure can be defined **recursively** (locally) as a collection of nodes (starting at a root node), where each node is a data structure consisting of a value, together with a list of references to nodes (the "children"), with the constraints that no reference is duplicated, and none points to the root.

A tree is a data structure made up of nodes or vertices and edges **without having any cycle**. The tree with no nodes is called the null or empty tree. A tree that is not empty consists of a root node and potentially many levels of additional nodes that form a hierarchy.
 
1. One root 
2. 1 -> N 
2. No cycle 
3. No two parents 
4. One component 

![Not a tree](https://i.imgur.com/SB1WIXq.png)

## ⚔️2. Use cases

- caculation about subtree

## 🤺3. Best Practices

- recursion (base case `None`)
- preorder, inorder, postorder recursively and iteratively

### corner case 

- root == `None`
- negative value 
- empty tree\ single node \ two nodes
- Very skewed tree (like a linked list).


## 😈4. More training

* [Ternary Expression to Binary Tree](https://repl.it/@WillWang42/Ternary-Expression-to-Binary-Tree?language=python3)

## 💬5. Explanation

## ⚠️6. FAQs