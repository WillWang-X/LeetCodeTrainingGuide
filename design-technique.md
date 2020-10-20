<h1 align="center">
<br>
  <a href="https://www.wikiwand.com/en/Binary_search_algorithm#/External_links"><img src="https://i.imgur.com/zaqIchQ.png" alt="design technique" width=400"></a>
  <br><br>
  Design Technique
  <br><br>
</h1>

No matter which programming language you use for programming, it is important to learn **algorithm design techniques** in data structures in order to be able to build **scalable** systems.

Selecting a **proper** design technique for algorithms is a **complex** but **important** task. Following are some of the main algorithm design techniques:


* **Brute Force**: DFS, BFS 
* Binary search
* Divide & Conquer, Dynamic Programming, Greedy 
* Decrease & Conquer，Transform & Conquer

| key 🔑 | typical problems👻 | video/gif 🎦 | notes 📒 |
| :-------- | :---------: | :----------: | :---------: |
| [DFS](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/dfs.md)| 🌟[46. Permutations](https://leetcode.com/problems/permutations/description/)  <br><br>👾[112 **Path**系列](https://leetcode.com/problems/path-sum/submissions/1), 👻[105. Construct](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/), 👹[329. topological](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/description/) |<img src="https://i.imgur.com/RVGtn22.gif" alt="DFS" width="200"/> <br> | [探测环](https://willwang-x.github.io/2018/02/shift)<br>前序遍历<br>非递归 <br>拓扑排序<br>树深<br>**DFS with Memo 913**<br> |
| [BFS](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/bfs.md) | 🌟[490.The Maze系列](https://leetcode.com/problems/the-maze/) <br><br> 👾[107 level](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/), 👻[200 island](https://leetcode.com/problems/number-of-islands/), 👹[269 alien](https://leetcode.com/problems/alien-dictionary)| <img src="https://i.imgur.com/c0F4gTc.gif" alt="bfs" width="200"/> | 遍历<br>块<br>最短路径<br>拓扑排序|
| [Binary Search](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/binary-search.md) | 🌟[33. Search in **Rotated** **Sorted** Array](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/description/) <br><br> 👾[35 insert](https://leetcode.com/problems/search-insert-position/), 👻[300 longest](https://leetcode.com/problems/longest-increasing-subsequence/), 👹[354 envelopes](https://leetcode.com/problems/russian-doll-envelopes/)  |<img src="https://i.imgur.com/7Wh8Jm3.gif" alt="binary search" width="200"/>  | 减治系列 <br> 搜索系列 |
| [Divide & conquer](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/divide-and-conquer.md) | 🌟[23. Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) <br><br>👾[53 Maximum](https://leetcode.com/problems/maximum-subarray/), 👻[932 Beautiful](https://leetcode.com/problems/beautiful-array/), 👹[4 Median](https://leetcode.com/problems/median-of-two-sorted-arrays/) |<img src="https://i.imgur.com/fMLtVzX.png" alt="divide and conquer" width="200"/> |mergesort |
| [DP](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/dp.md) | 🌟[Stock系列](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) <br><br> 👾[70 stairs](https://leetcode.com/problems/climbing-stairs/), 👻[416 subset](https://leetcode.com/problems/partition-equal-subset-sum/), 👹[140 words](https://leetcode.com/problems/word-break-ii/) | <img src="https://i.imgur.com/KHu7mL1.jpg" alt="dynamic programming" width="200"/> <br> by [Pramp](https://blog.pramp.com/how-to-solve-any-dynamic-programming-problem-603b6fbbd771) | **choice**<br> variable<br>sequence<br>最短路径(TSP)<br>for/recursive<br>counting<br>**string**<br>**DP2DFS**<br>**背包**416<br>**股票**系列|
| [Greedy](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/greedy.md) | 🌟[402. Remove K Digits系列](https://leetcode.com/problems/remove-k-digits/)<br><br> 👾[455 cookies](https://leetcode.com/problems/assign-cookies/), 👻[253 rooms](https://leetcode.com/problems/meeting-rooms-ii/), 👹[135 candy](https://leetcode.com/problems/candy/) | <img src="https://i.imgur.com/1aDfDOW.png" alt="greedy" width="200"/> <br> minimum coins| **Heap**<br>Prim<br>Kruskal<br>归纳<br>演绎| 
| [Decrease & conquer](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/decrease-%26-conquer.md) | 🌟[240. Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)<br><br> [169 majority](https://leetcode.com/problems/majority-element/), [78 subsets](https://leetcode.com/problems/subsets/), 👹[4 median](https://leetcode.com/problems/median-of-two-sorted-arrays/) | <img src="https://i.imgur.com/gAbsr24.gif" alt="decrease and conquer / insertion sort" width="200"/> <br> by [Anany](https://www.amazon.com/Introduction-Design-Analysis-Algorithms-3rd/dp/0132316811/ref=sr_1_1?s=books&ie=UTF8&qid=1548866452&sr=1-1&keywords=Introduction+to+the+Design+and+Analysis+of+Algorithms) | 减一技术<br>binary search <br> size-decrease<br>合并排序<br>快速排序|
| [Transform & conquer](https://github.com/willwang-x/algorithms-with-illustrations/blob/master/cornerstone/transform-%26-conquer.md) |  |  <img src="https://i.imgur.com/1kbXnP2.gif" alt="Transform & conquer / heap sort" width="200"/> <br>heap sort | 推排序<br>预排序|
