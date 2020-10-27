# Matrix

## 📝1. Basics

## ⚔️2. Use cases

- component: [island 系列](https://leetcode.com/problems/number-of-islands/)
- shortest path: [maze 系列](https://leetcode.com/problems/the-maze/) 
- simulation: [Spiral matrix 系列](https://leetcode.com/problems/spiral-matrix-iii/)
- search: [240 search a 2D matrix](https://leetcode.com/problems/search-a-2d-matrix-ii/), [542](https://leetcode.com/problems/01-matrix/)

## 🤺3. Best Practices 

- edge case 
- seen
- neighbors
- component
- shortest path (heap)


#### edge case: [], [[]]

``` python 
if not matrix or not matrix[0]:
	return 0
```

#### visited / seen

``` python
if not matrix: 
	raise "ValueError"
R = len(matrix)
C = len(matrix[0])
seen = [[False] * C for _ in range(R)]
```

#### traversal

``` python
def max_increase_keeping_skyline(grid: List[List[int]]) -> int:
    row_maxes = [max(row) for row in grid]
    col_maxes = [max(col) for col in zip(*grid)]
    
    return sum(min(row_maxes[r], col_maxes[c]) - val 
              for r, row in enumerate(grid)
              for c, val in enumerate(row))
              
# row, col = the best name   
```

- Try [807](https://leetcode.com/problems/max-increase-to-keep-city-skyline/)

#### get valid neighbors

``` python 
def neighbor(r, c): 
	for nr, nc in ((r-1,c),(r,c-1),(r+1,c),(r,c+1)):
	    if 0 <= nr < R and 0 <= nc < C:
	        yield nr, nc

def unseen_neighbor(r, c): 
	for nr, nc in ((r-1,c),(r,c-1),(r+1,c),(r,c+1)):
	    if 0 <= nr < R and 0 <= nc < C and not seen[nr][nc]:
	        yield nr, nc    
```

#### get component 

``` python
# matrix[x][y] == 1
# flipped `1` to `0` after visiting
def dfs(x, y):
	matrix[x][y] = 0 # or `0`
	for i, j in neighbor(x, y):
		if not seen[i][j]: dfs(i, j)
	return 1 
```

#### shortest path 

``` python
def shortest_dist(maze: List[List[int]], start: List[int], destination: List[int]) -> int:
    R, C = len(maze), len(maze[0])
    
    seen = [[False] * C for _ in range(R)]
    heap = [(0, start[0], start[1])]
    
    while heap:
        d, x, y = heapq.heappop(heap)
        # edge case 
        if seen[x][y]: continue 
        seen[x][y] = True 
        # base case 
        if [x, y] == destination:
            return d
        # general case 
        for step, i, j in neighbor(x, y, maze):
            heapq.heappush(heap, (d + step, i, j))
    return -1
```
``` python    
def neighbor(r, c, maze):
    R, C = len(maze), len(maze[0])
    for dr, dc in [(0, -1), (0, 1), (1, 0), (-1, 0)]:
        nr, nc, step = r, c, 0
        while 0 <= nr + dr < R and 0 <= nc + dc < C and maze[nr+dr][nc+dc] == 0:
            nr, nc = nr+dr, nc+dc
            step += 1
        yield step, nr, nc  
```

- Try: [505](https://leetcode.com/problems/the-maze-ii/)

## 😈4. More training

- [240. Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)
- [378. Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)
- [505. The Maze II](https://leetcode.com/problems/the-maze-ii/)
- [542. 01 Matrix](https://leetcode.com/problems/01-matrix/)
- [885. Spiral Matrix III](https://leetcode.com/problems/spiral-matrix-iii/)
- [1030. Matrix Cells in Distance Order](https://leetcode.com/problems/matrix-cells-in-distance-order/)

## 💬5. Explanation 

## ⚠️6. FAQs 