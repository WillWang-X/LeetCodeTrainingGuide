<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/List_of_data_structures">
  <img src="https://i.imgur.com/7ZBfuh5.png" alt="data structure from wiki" width=42%">
  </a>
  <br><br>
Data Structure
  <br><br>
</h1>

> In computer science, a data structure is a data **organization**, **management**, and **storage** format that enables efficient **access** and **modification**. 
> 
> More precisely, a data structure is a **collection** of data values, the **relationships** among them, and the functions or **operations** that can be applied to the data. [[wiki](https://www.wikiwand.com/en/Data_structure)]

Here are some notable [data structures](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/data-structure.md): 

* Bit, String
* Arrays, Linked 
	* Hash table 
* **Queue**, **Stack**
* Set (Disjoint-set)
* Graph
* Trees
	* Binary Search Tree, **Heap**, Trie
	* Binary Indexed Tree, Segment Tree

| key🔑 | typical problems🌟 | intuition🌠 | tags🏷 |
| :-------- | :---------: | :----------: | :---------: |
| [Bit](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/bit.md)| 🌟[268. Missing Number](https://leetcode.com/problems/missing-number/)<br><br>👾[371. sum](https://leetcode.com/problems/sum-of-two-integers/), 👻[260. single](https://leetcode.com/problems/single-number-iii/), 👹[411. unique](https://leetcode.com/problems/minimum-unique-word-abbreviation/) | <img src="https://i.imgur.com/S6s8tb6.png" alt="bit" width="200"/> | |
| [String](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/string.md) | 🌟[12. Integer to Roman](https://leetcode.com/problems/integer-to-roman/) <br><br> 👾[67. add](https://leetcode.com/problems/add-binary/),👻[6. zigzag](https://leetcode.com/problems/zigzag-conversion/), 👹[336. **palindrome**系列](https://leetcode.com/problems/palindrome-pairs/) | <img src="https://i.imgur.com/1MzpsFt.png" alt="string" width="200"/> | anagram<br />palindrome<br> [KMP⚡️](http://whocouldthat.be/visualizing-string-matching/)|
| [Array](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/array.md) | 🌟[75. Sort Colors](https://leetcode.com/problems/sort-colors/description/) <br><br> 👾[26 duplicate](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/), 👻[31. permute](https://leetcode.com/problems/next-permutation/description/), 👹[41. missing](https://leetcode.com/problems/first-missing-positive/description/) | <img src="https://i.imgur.com/mWp1gdR.gif" alt="array" width="200"/> <br> | off-by-1, <br> from the back <br> matrix|
| [Hash Table](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/hashmap.md)| 🌟[325. Maximum Size Subarray Sum Equals k 系列](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/) <br><br> 👾[1. sum系列](https://leetcode.com/problems/two-sum/), 👻[49. group](https://leetcode.com/problems/group-anagrams/), [149. points](https://leetcode.com/problems/max-points-on-a-line/)|  <img src="https://i.imgur.com/l1598o9.gif" alt="hash" width="200"/> <br> by [Inside python dict](https://just-taking-a-ride.com/inside_python_dict/chapter2.html)| |
| [Linked List](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/linked-list.md)|🌟[25. Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/) <br><br> 👾[141. cycle](https://leetcode.com/problems/linked-list-cycle/description/), 👻[2. add](https://leetcode.com/problems/add-two-numbers/description/), 👹[146. LRU](https://leetcode.com/problems/lru-cache/description/) | <img src="https://i.imgur.com/iCUdnOe.png" alt="linkedlist" width="200"/> | 加删查转 <br>虚头虚尾<br>快慢指针 |
| [Queue](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/queue.md)| [849?](https://leetcode.com/problems/maximize-distance-to-closest-person/description/)<br><br> 👻[346. stream](https://leetcode.com/problems/moving-average-from-data-stream/), ?, [363. rectangle](https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/)|  <img src="https://i.imgur.com/VFhfyxe.png" alt="queue" width="200"/> |FIFO<br>+BFS|
|[Stack](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/stack.md)|🌟[84. Largest Rectangle in Histogram系列](https://leetcode.com/problems/largest-rectangle-in-histogram/)<br><br> 👾[20. parentheses系列](https://leetcode.com/problems/valid-parentheses/), 👻[394. decode](https://leetcode.com/problems/decode-string/), 👹[770. calculator系列](https://leetcode.com/problems/basic-calculator-iv/)|<img src="https://i.imgur.com/W0LDr8g.png" alt="stack" width="200"/> <br>  | <br>LIFO<br>+DFS <br>**最近最大**<br>存做后用<br>离散有序|
| [Disjoint Set](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/union-find.md)| 🌟[305. Number of Islands II](https://leetcode.com/problems/number-of-islands-ii/) <br><br> x, 👻[130 regions](https://leetcode.com/problems/surrounded-regions/), 👹[803 falling](https://leetcode.com/problems/bricks-falling-when-hit/) |  <img src="https://i.imgur.com/OldUfa1.jpg" alt="disjoint set / union-find" width="200"/> <br> by [Union Find](https://www.youtube.com/watch?v=0jNmHPfA_yE) | |
|[Graph](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/graph.md)||<img src="https://i.imgur.com/ArTcbU2.png" alt="graph" width="200"/>||
| [Tree](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/tree.md) | [261. Graph Valid Tree](https://leetcode.com/problems/graph-valid-tree/)<br><br> | <img src="https://i.imgur.com/SB1WIXq.png" alt="tree" width="200"/> | insert<br />delete<br />change<br />cycle<br />search<br> |
| [Binary Tree](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/binary-tree.md)| 🌟[105. **Construct** BT from Preorder and Inorder Traversal系列](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)<br><br>👾[617. merge系列](https://leetcode.com/problems/merge-two-binary-trees/), 👻[199. view系列](https://leetcode.com/problems/binary-tree-right-side-view/), 👹[124. path-sum系列](https://leetcode.com/problems/binary-tree-maximum-path-sum/) | <img src="https://i.imgur.com/Q1zYUjH.gif" alt="binary tree" width="200"/> | **recursive**<br>操作<br>查看<br>计算<br>|
| [Binary Search Tree](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/binary-search-tree.md)|🌟[230. Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/) <br><br> 👾[108. convert](https://leetcode.com/problems/convert-bst-to-greater-tree/), 👻[173. iterator](https://leetcode.com/problems/binary-search-tree-iterator/), [99. recover](https://leetcode.com/problems/recover-binary-search-tree/) | <img src="https://i.imgur.com/oAQtYTl.gif" alt="binary search tree" width="200"/> | 中序遍历|
| [Heap](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/heap.md) | 🌟[407. Trapping Rain Water II](https://leetcode.com/problems/trapping-rain-water-ii/description/) <br><br> 👾[743. delay](https://leetcode.com/problems/network-delay-time/), 👻[215. kth](https://leetcode.com/problems/kth-largest-element-in-an-array/description/), 👹[857. workers](https://leetcode.com/problems/minimum-cost-to-hire-k-workers/) | <img src="https://i.imgur.com/l7hnVq8.gif" alt="trapping-rain-water-2-heap from https://youtu.be/cJayBq38VYw" width="200"/> <br>[407](https://youtu.be/7niUr7LlviY) | LI**B**O<br>+Greedy<br> |
|[Trie](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/trie.md)|🌟[212. Word Search II](https://leetcode.com/problems/word-search-ii/)<br><br>👾[720. longest](https://leetcode.com/problems/longest-word-in-dictionary/),👻[421. XOR](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/),👹[642. autocomplete](https://leetcode.com/problems/design-search-autocomplete-system/description/) | <img src="https://i.imgur.com/w7j1TTW.gif" alt="trie" width="200"/> ||

