# [54](https://leetcode.com/problems/spiral-matrix/). Spiral Matrix

## Ideas

* simulation

## Code

### v0.2

``` python
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        if not matrix: return []
        res = []
        m, n = len(matrix), len(matrix[0])
        u, d, l, r = 0, m -1, 0, n - 1
        while u < d and l < r: 
            res += [matrix[u][j] for j in range(l, r)]
            res += [matrix[i][r] for i in range(u, d)]
            res += [matrix[d][j] for j in range(r, l, -1)]
            res += [matrix[i][l] for i in range(d, u, -1)]
            u, d, l, r = u + 1, d - 1, l + 1, r - 1
        if l == r:
            res += [matrix[i][r] for i in range(u, d + 1)]
        elif u == d:
            res += [matrix[u][j] for j in range(l, r + 1)]
        return res          
```

## Test

```
[[1,2,3,4],[5,6,7,8],[9,10,11,12]]
```