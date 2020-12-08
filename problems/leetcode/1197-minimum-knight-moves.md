<h1 align="center">
<br>
	<a href="https://leetcode.com/problems/minimum-knight-moves/">
  <img src="https://i.imgur.com/bj4He88.png" alt="intuition of problem" width=42%">
  </a>
  <br><br>
1197. Minimum Knight Moves  
  <br><br>
</h1>



## What

### Description

In an infinite chess board with coordinates from `-infinity` to `+infinity`, you have a knight at square `[0, 0]`. Return **the minimum number of steps** needed to move the knight to the square `[x, y]`. 

``` python
# destination pos  -> minimum number of steps from `[0, 0]`
# int, int         -> int 
I: x = 2, y = 1
O: 1
Explanation: [0, 0] → [2, 1]
```

### Clarification

* A knight has **8 possible moves** it can make, as illustrated below. Each move is two squares in a **cardinal direction**, then one square in an **orthogonal direction**.
* It is guaranteed the answer exists.



## How 

### Idea

* typical [BFS](https://www.wikiwand.com/en/Breadth-first_search)
* **DP**: dp(x, y) = min (dp(x-1, y-2), dp(x-2, y-1)) + 1
	* Domain knowledge: The key observation is that we do not need to distinguish x and y, and we don't care whether x and y are positive or negative at all.

 
### Example

```
Input: x = 5, y = 5
Output: 4
Explanation: [0, 0] → [2, 1] → [4, 2] → [3, 4] → [5, 5]
```

### Code
 
#### [BFS](https://www.wikiwand.com/en/Breadth-first_search)
 
``` python
class Solution:
    def minKnightMoves(self, x: int, y: int) -> int:
        queue = collections.deque([(0, 0, 0)])
        discovered = set([(0, 0)])
        while queue:
            i, j, depth = queue.popleft()
            if self.is_goal(i, j, x, y):
                return depth
            for ni, nj in self.neighbor(i, j):
                if (ni, nj) not in discovered: 
                    discovered.add((ni, nj))
                    queue.append((ni, nj, depth+1))

    def is_goal(self, i, j, x, y):
        return i == x and j == y
    
    def neighbor(self, i, j):
        moves = ((2, 1), (1, 2), (-1, 2), (-2, 1), (-2, -1), (-1, -2), (1, -2), (2, -1))
        for di, dj in moves:
            yield i + di, j + dj
```

#### DP 

``` python
from functools import lru_cache
class Solution:
    def minKnightMoves(self, x: int, y: int) -> int:
        @lru_cache(None)
        def dp(x, y):
            if x + y == 0:
                return 0
            elif x + y == 1:
                return 3
            elif x + y == 2:
                return 2
            return min(dp(abs(x - 1), abs(y - 2)), dp(abs(x - 2), abs(y - 1))) + 1
        return dp(abs(x), abs(y))
```

### Test

```
2
1
5
5
```