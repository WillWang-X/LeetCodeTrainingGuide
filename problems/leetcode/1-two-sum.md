# [1](https://leetcode.com/problems/two-sum/). Two Sum

## Problem

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

``` python
# array, target -> index, index
# [int], int    -> [int, int]
I: [2, 7, 11, 15], 9
O: [0, 1]
```

Constraints: 

* Only one valid answer exists.


## Ideas 

Brute force x hash table

* Iterate each element and check if its partner in our cache 
* cache: {num: index}

## Example

``` python
# [2, 11, 15, 7], 9
{2: 0}
{2: 0, 11: 1}
{2: 0, 11: 1, 15: 2}
```

## Code 

### v 0.1

``` python
# Time:  O(n)
# Space: O(n)

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        cache = {}
        for i, num in enumerate(nums):
            if target - num in cache:
                return [cache[target - num], i]
            cache[num] = i
        return []
```

## Test

```
[2,7,11,15], 9 -> [0,1]
```