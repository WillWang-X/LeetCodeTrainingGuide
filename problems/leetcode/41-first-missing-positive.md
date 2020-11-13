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

* **traverse** from 1 to **upper bound** and if the current element in our cache 
* if not, we found the **answer**, which is the first missing positive integer
* **cahce**: set(input) 

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
        upper_bound = max(0, max(nums)+1)
        cache = set(nums)
        for i in range(1, upper_bound):
            if i not in cache:
                return i
        return max(1, upper_bound)
```

### Reduce & conquer x Greedy?

``` python
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        length = len(nums)
        nums = self._mark(nums)
        for i in range(length):
            if nums[i] != "x": return i+1
        return length + 1
    
    def _mark(self, nums):
        i, length = 0, len(nums)
        while i < length:
            while nums[i] != "x" and 0 < nums[i] <= length and nums[nums[i]-1] != "x":
                pos = nums[i] - 1
                nums[pos], nums[i] = nums[i], nums[pos]
                nums[pos] = "x"
            i += 1
        return nums
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