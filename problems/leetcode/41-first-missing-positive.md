# [41](https://leetcode.com/problems/first-missing-positive/). First Missing Positive

## Problem 

Given an unsorted integer array, find the smallest missing positive integer.


``` python
# unsorted int array -> smallest missing postive integer
# [int]              -> int
I: [3,4,-1,1]
O: 2
```

Clarification:

* Your algorithm should run in O(n) time and uses constant extra space.

## Ideas

### Brute Force 

* set(list)
* traverse from 1 and if it is in our set until we find the first missing positive integer

### Reduce & conquer x Greedy?

* Put the num into their correct position and mark it as done `x`. 
* Iterate over list to find the first element which is not `x`, which means it is not marked as FOUND in our list.

## Example

``` python
# [2,4,-1,1,3,5] -> 6
0   2   [2, 4, -1, 1, 3, 5]
0   swap 2 and 4, marked pos 1 as 'x' 
0   swap 4 and 1, marked pos 3 as 'x' 
0   swap 1 and 1, marked pos 0 as 'x' 
----------
1   x   ['x', 'x', -1, 'x', 3, 5]
----------
2   -1  ['x', 'x', -1, 'x', 3, 5]
----------
3   x   ['x', 'x', -1, 'x', 3, 5]
----------
4   3   ['x', 'x', -1, 'x', 3, 5]
4   swap 3 and -1, marked pos 2 as 'x' 
----------
5   5   ['x', 'x', 'x', 'x', -1, 5]
5   swap 5 and -1, marked pos 4 as 'x' 
----------

```

## Code

### Brute Force 

``` python
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        if not nums: return 1
        up_bound = max(0, max(nums)+1)
        cache = set(nums)
        for i in range(1, up_bound):
            if i not in cache:
                return i
        return max(1, up_bound)
```

### Reduce & conquer x Greedy?

``` python
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        m = len(nums)
        i = j = 0
        while i < m:
            while nums[i] != "x" and 0 < nums[i] <= m and nums[nums[i]-1] != "x":
                pos = nums[i] - 1
                nums[pos], nums[i] = nums[i], nums[pos]
                nums[pos] = "x"
            i += 1
        
        for i in range(m):
            if nums[i] != "x":
                return i+1
        
        return m+1
    
```

## Test

```
[1,2,0]
[3,4,-1,1]
[2,4,-1,1]
[7,8,9,11,12]
[]
[-5]
```