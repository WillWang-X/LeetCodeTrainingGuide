<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Dynamic_programming">
  <img src="https://i.imgur.com/KHu7mL1.jpg" alt="dynamic programming" alt="Dynamic Programming" width=42%">
  </a>
  <br><br>
Dynamic Programming 
  <br><br>
</h1>



> Dynamic Programming is just a fancy way to say '**remembering stuff to save time later**'.
> 
> [How should I explain dynamic programming to a 4-year-old?](https://qr.ae/TWTdxP)

## 📝1. Basics

source: [Dynamic Programming – 7 Steps to Solve any DP Interview Problem](http://blog.refdash.com/dynamic-programming-tutorial-example/)

Consider using DP whenever you have to **make choices** to arrive at the solution, specifically, when the solution relates to subproblems.

In addition to optimization problems, DP is also **applicable** to **counting and decision problems**—any problem where you can express a solution recursively in terms of the same computation on smaller instances.

Although conceptually DP involves recursion, often for efficiency the cache is **built "bottom-up"**, i.e., iteratively. 

To save space, **cache space** may be **recycled** once it is known that a set of entries will not be looked up again. 

Sometimes, **recursion may out-perform a bottom-up DP** solution, e.g., when the solution is found early or subproblems can be **pruned** through bounding.


## ⚔️2. Use cases

- memoization
- choices: [322](https://leetcode.com/problems/coin-change/description/)
- add one variable: [1035](https://leetcode.com/problems/uncrossed-lines/)
- more variables
- sequence alignment 
- shortest paths: [787](https://leetcode.com/problems/cheapest-flights-within-k-stops/)
- counting: [91](https://leetcode.com/problems/decode-ways/)

---

- [**Longest common subsequence**](https://leetcode.com/problems/uncrossed-lines/): top down or bottom up, O(n) - O(1)
- choice: 120, 97, 174, [221 Matrix], 903, **322**
- variable: 188, 474,
- sequence aligment: [300](https://leetcode.com/problems/longest-increasing-subsequence/description/) , 152
- shortest path: 943 
- counting: 96, 16, 70, 96
- string: 5 
- DFS -> DP: 139, 678, 464 
- 背包系列
- 股票系列


重叠子问题 选择 增加一个变量 多个变量 数列问题 最短路径

* Fibonacci 经典型
* Choices
* Add variables (背包系列)
* Sequence alignment
* Shortest Paths

Other:

* ❶ Fibonacci 一步两步: f(n) = f(n-1) + f(n-2)
* ❷ 96 Unique Binary Search Trees
* ❸ Sequence alignment
* ❹ Add variables (背包系列 🎒 )
* ❺ choices
* ❻ Maximum Product Subarray VS Maximum Sum Subarray

## 🤺3. Best Practices

- top down 
- bottom up
- 2D to 1D
- 1D to O(1)

#### top down 

``` python
def min_edit_dist(self, word1: str, word2: str) -> int:
    memo = {}
    def dp(i, j):
        if i == len(word1) or j == len(word2):
            memo[(i,j)] = max(len(word1) - i, len(word2) - j)
        if (i, j) not in memo:
            if word1[i] == word2[j]:
                memo[(i, j)] = dp(i+1, j+1)
            else:
                memo[(i, j)] = 1 + min(dp(i+1, j), dp(i, j+1), dp(i+1, j+1))
        return memo[(i,j)]
    return dp(0, 0)
```

#### bottom up 

``` python
def min_edit_dist(self, word1: str, word2: str) -> int:
    M, N = len(word2), len(word1)
    
    # array to store the convertion history
    dp = [[0] * (M + 1) for _ in range(N + 1)]
    
    # init boundaries
    for i in range(N + 1):
        dp[i][0] = i
    for j in range(M + 1):
        dp[0][j] = j
    
    # DP compute
    for i in range(1, N+1):
        for j in range(1, M+1):
            if word1[i-1] == word2[j-1]:
                dp[i][j] = dp[i-1][j-1]
            else:
                dp[i][j] = 1 + min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1])
    return dp[-1][-1]
```

#### LCS

``` python
def longest_common_subsquence(A: List[int], B: List[int]) -> int:
    dp, m, n = collections.defaultdict(int), len(A), len(B)
    for i in range(m):
        for j in range(n):
            dp[i, j] = max(dp[i - 1, j - 1] + (A[i] == B[j]), 
				           dp[i - 1, j], 
				           dp[i, j - 1])
    return dp[m - 1, n - 1]
```

- Try [516](https://leetcode.com/problems/longest-palindromic-subsequence/), [1035](https://leetcode.com/problems/uncrossed-lines/), 


## 😈4. More training

- [1035. Uncrossed Lines](https://leetcode.com/problems/uncrossed-lines/): Typical! LCS
* 62 Unique Paths
* 70 Climbing Stairs ❶
* 120 Triangle
* 174 Dungeon Game ❷
* 123 Best Time to Buy and Sell Stock III
* 53 Maximum Subarray(与股票对应，完全对应)
* 474 Ones and Zeroes ❸
* 97 Interleaving String
* 115 Distinct Subsequences ❹
* 139 Word Break ❺
* 96 Unique Binary Search Trees
* 152 Maximum Product Subarray
* 3 Longest Substring Without Repeating Characters
* 53 Maximum Subarray
* 152 Maximum Product Subarray
* 416 Partition Equal Subset Sum
* 474 Ones and Zeroes
* 600 Non-negative Integers without Consecutive Ones

## 💬5. Explanation 

> Define your recurrence relation and base cases. Besides, try to improve your space complexity if possible.

[LC91 Decode Variations](https://www.pramp.com/challenge/r1Kw0vwG6OhK9AEGAy6L) (in terms of, only reference)

* **Let** dp(i) **be the answer for the string** S[i:]. We can calculate dp(i) **in terms of** dp(i+1) and dp(i+2).  
* If S[i] == 0 ... 2 ... > 2...  Putting this all together ...
* Of course, **since at each step** we only **reference** dp[i+1] and dp[i+2], we could **store these as variables** `first` and `second`. This means we do not need to store the entire array.

[LC72 Edit Distance](https://repl.it/@WillWang42/edit-distance) (two steps, either...or..., in general, recursively)

* Our solution will be built in two steps: first we’ll **find the editing distance**, and then **use it to construct the answer**. 
* First, let `dp(i, j)` = the minimum number of edits required **for the problem with strings** `source[i:]` and `target[j:]`. 
* We will perform what is known as “top-down dynamic programming.” What this means is: Since `dp(i, j)` may depend only on the values of `source[i]`, `target[j]`, `dp(i+1, j)`, `dp(i, j+1)`, and `dp(i+1, j+1)`, we can write a function `dp(i, j)` that returns the desired answer **recursively** **in terms of** these values. 
* **In general**, when `source[i] == target[j]`, then `dp(i, j) = dp(i+1, j+1)`, because we simply write `source[i]`. When `source[i] != target[j]`, then we **either** edited `source[i]` (subtraction) and **have the problem of transforming** `source[i+1:]` to `target[j:]` left over (which has answer `dp(i+1, j)`), **or** we edited `target[j]` (addition) and have the problem of transforming `source[i:]` to `target[j+1:]` left over (which has answer `dp(i, j+1)`).
* **Constructing the Answer**
* Now we need to build our answer. We should **iterate through the source and target**, and in each step decide whether we need to delete or add another letter.
* To figure this out, we need to **leverage this information** available in `dp(i, j)`. When we have a decision to make between subtracting `source[i]` or adding `target[j]`, we will use our knowledge of the minimum edit distances `dp(i+1, j)` and `dp(i, j+1)` to make our decision.


## ⚠️6. FAQs
