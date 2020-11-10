# [200](https://leetcode.com/problems/number-of-islands/). Number of Islands

## Ideas

Toggle each land(1->0) while DFS/BFS. 

- DFS
- BFS
- Union Find 

## Example

```
I: [["1","1","1","1","0"],["1","1","0","1","0"],["1","1","0","0","0"],["0","0","0","0","0"]]
O: 1
```

``` python
Start: [['1', '1', '1', '1', '0'], ['1', '1', '0', '1', '0'], ['1', '1', '0', '0', '0'], ['0', '0', '0', '0', '0']]
First: [['0', '0', '0', '0', '0'], ['0', '0', '0', '0', '0'], ['0', '0', '0', '0', '0'], ['0', '0', '0', '0', '0']]

```

## Code

### v0.1

``` python
# Time: O(n^2) where n = len(grid)
# Space: O(1)

class Solution:   
    def __init__(self):
        self.grid = []
        self.R = 0
        self.C = 0
    
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid: return 0
        self.grid, self.R, self.C = grid, len(grid), len(grid[0]) 
                     
        res = 0
        for i in range(self.R):
            for j in range(self.C):
                if self.grid[i][j] == "1": res += self.dfs(i, j)
        return res
    
    def dfs(self, x, y):
        self.grid[x][y] = "0"
        for dx, dy in self.neighbor(x, y):
            if self.grid[dx][dy] == "1": self.dfs(dx, dy)
        return 1   

    def neighbor(self, r, c): 
        for nr, nc in ((r-1,c),(r,c-1),(r+1,c),(r,c+1)):
            if 0 <= nr < self.R and 0 <= nc < self.C:
                yield nr, nc
```