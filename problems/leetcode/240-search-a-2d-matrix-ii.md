# [240](https://leetcode.com/problems/search-a-2d-matrix-ii/). Search a 2D Matrix II


## Problem 

Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:

* Integers in each row are **sorted** in **ascending** from left to right.
* Integers in each column are **sorted** in **ascending** from top to bottom.

``` python
# matrix, target -> found?
# [[int]], int   -> Boolean
I: [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]] 5
O: true
```

Clarification:

* 


## Ideas

**Decrease and conquer**

* Start from right and top
	* if target < x, move left
	* elif target > x, move down
	* else, return True 


## Example 

``` python
# [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]] 
# target = 5

[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]

i j matrix[i][j]
0 4 15
0 3 11
0 2 7
0 1 4
1 1 5

```


## Code 

### v 0.1


``` python
class Solution:
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        if not matrix: return False 
        
        i, j = 0, len(matrix[0]) - 1
        while 0 <= i < len(matrix) and 0 <= j < len(matrix[0]):
            if target < matrix[i][j]:
                j -= 1
            elif target > matrix[i][j]:
                i += 1
            else:
                return True 
        return False 
``` 

## Test 

```
[[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]]
5
```
