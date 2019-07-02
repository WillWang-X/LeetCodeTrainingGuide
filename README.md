<h1 align="center">
<br>
  <a href="https://github.com/willwang-x/algorithms-with-illustrations"><img src="https://i.imgur.com/8YKuHaC.png" alt="Aogrithms with Illustration" width=200"></a>
  <br>
    <br>
  Aogrithms with Illustration
  <br><br>
</h1>

> When you understand something, then you can find the math to express that understanding. The math doesn't provide the **understanding**. The purpose of computing is **insight**, not numbers. The only real valuable thing is **intuition**.  
> 
> by *Leslie Lamport & Richard Hamming & Albert Einstein*


## Features

- **Insight**: intuition, connect, debug
- **Core**: basics, application, best practice, typical problems, explanation, Q&A
- **Map**: problem type -> (data structure, design techniques) -> ways of thinking

## Lists 

### [problem type](https://www.wikiwand.com/en/List_of_algorithms) (11)

source: [wiki](https://www.wikiwand.com/en/Algorithm#/By_field_of_study)

Every field of science has its own problems and needs efficient algorithms. Related problems in one field are often studied together.

Fields tend to overlap with each other, and algorithm advances in one field may improve those of other, sometimes completely unrelated, fields. For example, dynamic programming was invented for optimization of resource consumption in industry but is now used in solving a broad range of problems in many fields.

| Field            | Algorithms   |
| ----------          | ------------ |
|[**Combinatorial**](https://www.wikiwand.com/en/Combinatorics)/3|General combinatorial, Graph, [Sequence](https://www.wikiwand.com/en/Sequences)|
|**/general**|
| **/graph/5**|Graph drawing, Network theory, **Routing for graphs**, Graph search, Subgraphs|
| //basics| coloring, Hopcroft–Karp, Hungarian, Prüfer coding, Tarjan's, [topological-sort](https://repl.it/@WillWang42/graph-topological-sort)|
| //drawing| |
| //network theory| |
| //routing| MST(Borůvka, [prim](https://repl.it/@WillWang42/MST-Prim), [kruskal](https://repl.it/@WillWang42/MST-Kruskal), Reverse-delete)|
| //search| |
| //subgraph| |
|**/sequence/9**|matching, selection, search, merge, permutations, alignment, sorting, subsequences, substrings|
|//[sorting](https://www.wikiwand.com/en/Sorting_algorithm) |[quicksort](https://repl.it/@WillWang42/quick-sort), [mergesort](https://repl.it/@WillWang42/merge-sort), [insertion-sort](https://repl.it/@WillWang42/insertion-sort), heap-sort, counting-sort, [selection-sort](https://repl.it/@WillWang42/selection-sort)|
|//[selection](https://www.wikiwand.com/en/Selection_algorithm)|[quickselect](https://repl.it/@WillWang42/quickselect), introselect, median of medians|
|//permutations|[Fisher–Yates](https://repl.it/@WillWang42/Fisher-Yates-shuffle),|
|//[substrings](https://www.wikiwand.com/en/Substring)|Longest common substring, substring search(Aho–Corasick, Boyer–Moore, [KMP](https://repl.it/@WillWang42/substring-KMP), Rabin–Karp, Zhu–Takaoka), Ukkonen-suffix-tree, [matching wildcards](https://repl.it/@WillWang42/substring-matching-wildcards)|
|[**Computational Math**](https://www.wikiwand.com/en/Computational_mathematics)/|Computer algebra, Geometry, Number theoretic algorithms, Numerical algorithms, [Optimization](https://www.wikiwand.com/en/Mathematical_optimization)|
|/Optimization|...dynamic programming...|
|//-[dynamic programming](https://www.wikiwand.com/en/Dynamic_programming#/Algorithms_that_use_dynamic_programming)|string (longest common subsequence, longest increasing subsequence, longest common substring, edit distance), Kadane-maximum-subarray, <br> graph (Viterbi, Floyd, TSP, Bellman–Ford), <br> pseudo-polynomial time([subset sum](https://repl.it/@WillWang42/dp-subset-sumåååå), [knapsack](https://repl.it/@WillWang42/dp-knapsack), partition), <br> interval scheduling<br> [segmented least square](https://repl.it/@WillWang42/segmented-least-squares)   |
|[**Computational science**](https://www.wikiwand.com/en/Computational_science)|
|...|





### data structrue

<h1 align="center">
  <a href="https://www.wikiwand.com/en/List_of_data_structures"><img src="https://i.imgur.com/iJ5pGpD.png" alt="list of data structures"></a>
</h1>


- binary/bit, string, array(hash), linked list, queue, stack 
- set: disjoint set
- graph
- tree: binary tree, binary search tree, heap, trie, binary indexed tree, segment tree
- sequence, hash

| key 🔑 | typical problems👻 | video/gif 🎦 | notes 📒 |
| :-------- | :---------: | :----------: | :---------: |
| [Data Structure](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/data-structure.md)⛓️| 🌟**举一**(Typical)<br><br>反三<br>(👾easy, 👻medium, 👹hard) | <img src="https://i.imgur.com/OUh1FBf.png" alt="data structure mindmap" width="200"/> <br> |  逻辑结构<br>存储结构<br>**操作**方式|
| [Bit](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/bit.md)| 🌟[268. Missing Number](https://leetcode.com/problems/missing-number/)<br><br>👾[371 sum](https://leetcode.com/problems/sum-of-two-integers/), 👻[260 single](https://leetcode.com/problems/single-number-iii/), [411 unique](https://leetcode.com/problems/minimum-unique-word-abbreviation/) | <img src="https://i.imgur.com/S6s8tb6.png" alt="bit" width="200"/> | |
| [String](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/string.md) | 🌟[12. Integer to Roman](https://leetcode.com/problems/integer-to-roman/) <br><br> 👾[67 add](https://leetcode.com/problems/add-binary/),👻[6 zigzag](https://leetcode.com/problems/zigzag-conversion/), [336 **palindrome**系列](https://leetcode.com/problems/palindrome-pairs/) | <img src="https://i.imgur.com/1MzpsFt.png" alt="string" width="200"/> | anagram<br />palindrome<br> [KMP⚡️](http://whocouldthat.be/visualizing-string-matching/)|
| [Array](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/array.md) | 🌟[75. Sort Colors](https://leetcode.com/problems/sort-colors/description/) <br><br> 👾[26 duplicate](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/), 👻[31 permute](https://leetcode.com/problems/next-permutation/description/), [41 missing](https://leetcode.com/problems/first-missing-positive/description/) | <img src="x" alt="array" width="200"/> <br> | off-by-1, <br> from the back <br> matrix|
| [Hash](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/hashmap.md)| 🌟[325. Maximum Size Subarray Sum Equals k 系列](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/) <br><br> 👾[1 sum系列](https://leetcode.com/problems/two-sum/), 👻[49 group](https://leetcode.com/problems/group-anagrams/), [149 points](https://leetcode.com/problems/max-points-on-a-line/)|  <img src="https://i.imgur.com/l1598o9.gif" alt="hash" width="200"/> <br> by [Inside python dict](https://just-taking-a-ride.com/inside_python_dict/chapter2.html)| |
| [Linked List](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/linked-list.md)|🌟[25. Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/) <br><br> 👾[141 cycle](https://leetcode.com/problems/linked-list-cycle/description/), 👻[2 add](https://leetcode.com/problems/add-two-numbers/description/), 👹[146 LRU](https://leetcode.com/problems/lru-cache/description/) | <img src="x" alt="linkedlist" width="200"/> | 加删查转 <br>虚头虚尾<br>快慢指针 |
| [Queue](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/queue.md)| [849?](https://leetcode.com/problems/maximize-distance-to-closest-person/description/)<br><br> 👻[346 stream](https://leetcode.com/problems/moving-average-from-data-stream/), ?, [363 rectangle](https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/)|  <img src="https://i.imgur.com/VFhfyxe.png" alt="queue" width="200"/> |FIFO<br>+BFS|
|[Stack](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/stack.md)|🌟[84. Largest Rectangle in Histogram系列](https://leetcode.com/problems/largest-rectangle-in-histogram/)<br><br> 👾[20 parentheses系列](https://leetcode.com/problems/valid-parentheses/), 👻[394 decode](https://leetcode.com/problems/decode-string/), 👹[770 calculator系列](https://leetcode.com/problems/basic-calculator-iv/)|<img src="https://i.imgur.com/W0LDr8g.png" alt="stack" width="200"/> <br>  | <br>LIFO<br>+DFS <br>**最近最大**<br>存做后用<br>离散有序|
| [Set](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/set.md) | |  | |
| [Disjoint Set](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/union-find.md)| 🌟[305. Number of Islands II](https://leetcode.com/problems/number-of-islands-ii/) <br><br> x, 👻[130 regions](https://leetcode.com/problems/surrounded-regions/), 👹[803 falling](https://leetcode.com/problems/bricks-falling-when-hit/) |  <img src="https://i.imgur.com/OldUfa1.jpg" alt="disjoint set / union-find" width="200"/> <br> by [Union Find](https://www.youtube.com/watch?v=0jNmHPfA_yE) | |
|[Graph](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/graph.md)||<img src="https://i.imgur.com/ArTcbU2.png" alt="graph" width="200"/>||
| [Tree](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/tree.md)? | [261. Graph Valid Tree](https://leetcode.com/problems/graph-valid-tree/)<br><br> | <img src="https://i.imgur.com/SB1WIXq.png" alt="tree" width="200"/> | insert<br />delete<br />change<br />cycle<br />search<br> |
| [Binary Tree](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/binary-tree.md)| 🌟[105. **Construct** BT from Preorder and Inorder Traversal系列](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)<br><br>👾[617 merge系列](https://leetcode.com/problems/merge-two-binary-trees/), 👻[199 view系列](https://leetcode.com/problems/binary-tree-right-side-view/), 👹[124 path-sum系列](https://leetcode.com/problems/binary-tree-maximum-path-sum/) | <img src="https://i.imgur.com/Q1zYUjH.gif" alt="binary tree" width="200"/> | **recursive**<br>操作<br>查看<br>计算<br>|
| [Binary Search Tree](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/binary-search-tree.md)|🌟[230. Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/) <br><br> 👾[108 convert](https://leetcode.com/problems/convert-bst-to-greater-tree/), 👻[173 iterator](https://leetcode.com/problems/binary-search-tree-iterator/), [99 recover](https://leetcode.com/problems/recover-binary-search-tree/) | <img src="https://i.imgur.com/oAQtYTl.gif" alt="binary search tree" width="200"/> | 中序遍历|
| [Heap](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/heap.md) | 🌟[407. Trapping Rain Water II](https://leetcode.com/problems/trapping-rain-water-ii/description/) <br><br> 👾[743 delay](https://leetcode.com/problems/network-delay-time/), 👻[215 kth](https://leetcode.com/problems/kth-largest-element-in-an-array/description/), 👹[857 workers](https://leetcode.com/problems/minimum-cost-to-hire-k-workers/) | <img src="https://i.imgur.com/l7hnVq8.gif" alt="trapping-rain-water-2-heap from https://youtu.be/cJayBq38VYw" width="200"/> <br>[407](https://youtu.be/7niUr7LlviY) | LI**B**O<br>+Greedy<br> |
|[Trie](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/trie.md)?|🌟[212. Word Search II](https://leetcode.com/problems/word-search-ii/)<br><br>👾[720 longest](https://leetcode.com/problems/longest-word-in-dictionary/),👻[421 XOR](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/),👹[642 autocomplete](https://leetcode.com/problems/design-search-autocomplete-system/description/) | <img src="https://i.imgur.com/w7j1TTW.gif" alt="trie" width="200"/> ||


### design technique 

- DFS, BFS 
- Divide & conquer, DP, Greedy 
- Binary search，Decrease & conquer，Dynamic & conquer

| key 🔑 | typical problems👻 | video/gif 🎦 | notes 📒 |
| :-------- | :---------: | :----------: | :---------: |
| 算法思想❤️|  | <img src="https://i.imgur.com/9RJ5oGt.png" alt="algorithms insight" width="200"/> | ❤️❤️ |
| [DFS](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/dfs.md)| 🌟[46. Permutations](https://leetcode.com/problems/permutations/description/)  <br><br>👾[112 **Path**系列](https://leetcode.com/problems/path-sum/submissions/1), 👻[105. Construct](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/), 👹[329. topological](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/description/) |<img src="https://i.imgur.com/RVGtn22.gif" alt="DFS" width="200"/> <br> | [探测环](https://willwang-x.github.io/2018/02/shift)<br>前序遍历<br>非递归 <br>拓扑排序<br>树深<br>**DFS with Memo 913**<br> |
| [BFS](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/bfs.md) | 🌟[490.The Maze系列](https://leetcode.com/problems/the-maze/) <br><br> 👾[107 level](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/), 👻[200 island](https://leetcode.com/problems/number-of-islands/), 👹[269 alien](https://leetcode.com/problems/alien-dictionary)| <img src="https://i.imgur.com/c0F4gTc.gif" alt="bfs" width="200"/> | 遍历<br>块<br>最短路径<br>拓扑排序|
| [Divide & conquer](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/divide-and-conquer.md) | 🌟[23. Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) <br><br>👾[53 Maximum](https://leetcode.com/problems/maximum-subarray/), 👻[932 Beautiful](https://leetcode.com/problems/beautiful-array/), 👹[4 Median](https://leetcode.com/problems/median-of-two-sorted-arrays/) |<img src="https://i.imgur.com/fMLtVzX.png" alt="divide and conquer" width="200"/> |mergesort |
| [DP](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/dp.md) | 🌟[Stock系列](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) <br><br> 👾[70 stairs](https://leetcode.com/problems/climbing-stairs/), 👻[416 subset](https://leetcode.com/problems/partition-equal-subset-sum/), 👹[140 words](https://leetcode.com/problems/word-break-ii/) | <img src="https://i.imgur.com/KHu7mL1.jpg" alt="dynamic programming" width="200"/> <br> by [Pramp](https://blog.pramp.com/how-to-solve-any-dynamic-programming-problem-603b6fbbd771) | **choice**<br> variable<br>sequence<br>最短路径(TSP)<br>for/recursive<br>counting<br>**string**<br>**DP2DFS**<br>**背包**416<br>**股票**系列|
| [Greedy](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/greedy.md) | 🌟[402. Remove K Digits系列](https://leetcode.com/problems/remove-k-digits/)<br><br> 👾[455 cookies](https://leetcode.com/problems/assign-cookies/), 👻[253 rooms](https://leetcode.com/problems/meeting-rooms-ii/), 👹[135 candy](https://leetcode.com/problems/candy/) | <img src="https://i.imgur.com/1aDfDOW.png" alt="greedy" width="200"/> <br> minimum coins| **Heap**<br>Prim<br>Kruskal<br>归纳<br>演绎| 
| [Transform & conquer](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/transform-%26-conquer.md) |  |  <img src="https://i.imgur.com/1kbXnP2.gif" alt="Transform & conquer / heap sort" width="200"/> heap sort | |
| [Decrease & conquer](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/decrease-%26-conquer.md) | 🌟[240. Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)<br><br> [169 majority](https://leetcode.com/problems/majority-element/), [78 subsets](https://leetcode.com/problems/subsets/), 👹[4 median](https://leetcode.com/problems/median-of-two-sorted-arrays/) | <img src="https://i.imgur.com/gAbsr24.gif" alt="decrease and conquer / insertion sort" width="200"/> <br> by [Anany](https://www.amazon.com/Introduction-Design-Analysis-Algorithms-3rd/dp/0132316811/ref=sr_1_1?s=books&ie=UTF8&qid=1548866452&sr=1-1&keywords=Introduction+to+the+Design+and+Analysis+of+Algorithms) | 减一技术<br>binary search <br> size-decrease|
| [Binary Search](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/binary-search.md) | 🌟[33. Search in **Rotated** **Sorted** Array](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/description/) <br><br> 👾[35 insert](https://leetcode.com/problems/search-insert-position/), 👻[300 longest](https://leetcode.com/problems/longest-increasing-subsequence/), 👹[354 envelopes](https://leetcode.com/problems/russian-doll-envelopes/)  |<img src="https://i.imgur.com/7Wh8Jm3.gif" alt="binary search" width="200"/>  | 减治系列 <br> 搜索系列 |





### [way of thinking](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/mind.md)

- Induction & Deduction
- Recursion, Backtracking
- Two pointer, Siding window, Fast and slow
- Reverse thinking, Complement

| key 🔑 | typical problems👻 | video/gif 🎦 | notes 📒 |
| :-------- | :---------: | :----------: | :---------: |
| [思维方式](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/mind.md)🤔️ | 🤔️🤔️🤔️🤔️🤔️🤔️🤔️🤔️🤔️🤔️| 🤔️🤔️🤔️🤔️🤔️ | 🤔️🤔️ |
| [Recursion](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/recursion.md)? | 🌟[894. All Possible Full Binary Trees](https://leetcode.com/problems/all-possible-full-binary-trees/)<br><br> 👾[687 longest](https://leetcode.com/problems/longest-univalue-path/), [698 subsets](https://leetcode.com/problems/partition-to-k-equal-sum-subsets/), [248 strobogrammatic系列](https://leetcode.com/problems/strobogrammatic-number-iii/) | <img src="https://i.imgur.com/SAyEmMY.gif" alt="recursion" width="200"/> |+hashmap <br>递归公式<br>终止条件|
| [Backtracking](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/backtracking.md) | [39. Combination Sum](https://leetcode.com/problems/combination-sum/) <br><br>  [401 watch](https://leetcode.com/problems/binary-watch/), [22 parentheses](https://leetcode.com/problems/generate-parentheses/), [51 n-queens](https://leetcode.com/problems/n-queens/) | <img src="https://i.imgur.com/2Y3D3fI.gif" alt="backtracking" width="200"/> |集合<br>数迷<br>递归求解<br>**触底**反弹|
| [Two Pointers](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/two-pointers.md)| 🌟[18. 4Sum](https://leetcode.com/problems/4sum/) <br> <br> 👾[344 reverse](https://leetcode.com/problems/reverse-string/) 👻 [11 container](https://leetcode.com/problems/container-with-most-water/), [632 range](https://leetcode.com/problems/smallest-range/)|  <img src="https://i.imgur.com/8IL9VOS.png" alt="two pointers" width="200"/> <br> | |
| [Sliding Window](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/sliding-window.md) | 🌟[159. Longest Substring with At Most Two Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/description/) <br><br> 👾[26 remove](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/), 👻[19 node](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/), 👹[76 substring](https://leetcode.com/problems/minimum-window-substring/) | <img src="https://i.imgur.com/aQlMXk0.png" alt="sliding window" width="200"/> <br> |满足自省|
| fast and slow | [287. Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/description/) <br> <br> [283 move zeros](https://leetcode.com/problems/move-zeroes/description/),142,? | <img src="https://i.imgur.com/mcog6YC.jpg" alt="fast&slow pointers" width="200"/> |快慢指针|
| Reverse	thinking | 88， 795, 777, 👹803 | <img src="https://i.imgur.com/1ghXxOf.gif" alt="reverse thinking" width="200"/>  | |
| Complement | 🌟[930.Binary Subarrays With Sum](https://leetcode.com/problems/binary-subarrays-with-sum/) <br><br> 👾[283 move](https://leetcode.com/problems/move-zeroes/), 👻[921 add](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/), 👹? | <img src="https://i.imgur.com/0W32d8v.png" alt="complement" width="200"/> <br>[930](https://youtu.be/eRx56MI3Svo) | |





## Tools

Search:

- [Leetcode题目全集](https://workflowy.com/s/BZDH.sN6esXSMsn): 便于多个标签过滤查找
- [References](https://github.com/willwang-x/algorithms-with-illustrations/tree/master/references): Related books and courses.
- [Examples](https://github.com/keon/algorithms): Minimal and clean example implementations of data structures and algorithms in Python 3.
- [cosmos](https://github.com/OpenGenus/cosmos): Algorithms that run our universe
- [repl/algorithms-by-field](https://repl.it/repls/folder/algorithms-by-field)




Visualize: 

- [DS Visualizations](https://www.cs.usfca.edu/~galles/visualization/Algorithms.html)
- [Pythontutor](http://www.pythontutor.com/visualize.html#mode=edit): visualize Python, Java, JavaScript, C, C++, Ruby code **execution**
- [Graph](https://repl.it/@WillWang42/adjacency-list-2-matrix): create the graph from the adjacency list
- [imagus](https://chrome.google.com/webstore/detail/imagus/immpkjjlgappgfkkfieppnmlhakdmaab?hl=en): enlarge images from links with a mouse hover
- [Visualizer](https://algorithm-visualizer.org/): an interactive online platform that viualizes algorithms from code.
- [codelike](https://www.codelike.in/):  given most animated view of data structures like binary tree, binary search tree, avl tree, red black tree, linked list and so on.
- [mind-palace](https://workflowy.com/s/0-x-palace/wl1ogOpj0IU7juyl)

Language:

- [Python](https://github.com/OmkarPathak/pygorithm): A Python module for learning all major algorithms
- [Java](https://github.com/MeandNi/Algorithms4-Common): 算法4精华笔记，通俗理解
- [Javascript](https://github.com/trekhleb/javascript-algorithms): Implemented in JavaScript with explanations and links to further readings
- [Multi](https://github.com/davidxk/Algorithm-Implementations): Algorithm and data structure implementations in Python, C, C++ and Java


Practice: 

- [50+](https://hackernoon.com/50-data-structure-and-algorithms-interview-questions-for-programmers-b4b1ac61f5b0): give you enough of an idea of the kinds of questions you can expect in a real programming job interview
- [Leetcode](https://leetcode.com): Practice real interview questions
- [Pramp](https://www.pramp.com/invt/zpbVbZv7EYtGmrm10BqK): Mock Interview



## Thanks

* @caomingkai
* @davidxkHeapg