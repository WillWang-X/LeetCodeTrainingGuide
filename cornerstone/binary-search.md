
# Binary Search


![binary search](https://i.imgur.com/7Wh8Jm3.gif)

## 基础知识

Binary search is an efficient algorithm for finding an item from a sorted list of items. It works by repeatedly dividing in half the portion of the list that could contain the item, until you've narrowed down the possible locations to just one. 


## 典型应用

- find in sorted xx: 35 

## 最佳实践

- search insert position 
- identify the sorted part 

### search insert position (x < `target` for x in nums[:`i`])

``` python
def search_insert(nums: List[int], target: int) -> int:
    return bisect.bisect_left(nums, target)
```

``` python
def length_of_LIS(nums: List[int]) -> int:
    dp = [0] * len(nums)
    size = 0 
    for num in nums:
        i = bisect.bisect_left(dp, num, 0, size)
        dp[i] = num
        if i == size:
            size += 1
    return size 
```

### identify the sorted part [33](https://leetcode.com/problems/search-in-rotated-sorted-array/)

``` python
def search(nums: List[int], target: int) -> int:
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = left + (right - left) // 2
        if nums[mid] == target:
            return mid
        if nums[mid] >= nums[left]: # left part is sorted 
            if nums[left] <= target < nums[mid]: # in a sorted array 
                right = mid - 1
            else:
                left = mid + 1
        else:
            # right part is sorted
            if nums[mid] < target <= nums[right]: 
                left = mid + 1
            else:
                right = mid - 1
    return -1
```


## 木桩训练

- [81. Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)
- [300. Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)
- [354. Russian Doll Envelopes](https://leetcode.com/problems/russian-doll-envelopes/)

## Explain 

## Q & A 

## Thanks 

*  [python API: bisect](https://repl.it/@WillWang42/8-6-bisect)