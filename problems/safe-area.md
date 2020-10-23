# Count safe area 

## Problem 

Input: 

```
matrix = 
[
	[ 0, 0, 0, 0],
	[ 0, 0, 0, 1],
	[ 0, 0, 0, 1],
	[ 0, 0, 1, 0]
]
d = 2 	
```

Output: 

```
5
```

Explanation: 

Given a matrix m*n with 0 = empty safe, 1 = enemy, please answer how many  `d * d` safe areas?


## Ideas

* brute force: O(M * N * D * D)
* Or use a extra matrix to store info, which can tell safe list that ends with the index i. O(M * N * D)
* Or use **prefix sum method**, which may reduce time compleixity to O(M * N)