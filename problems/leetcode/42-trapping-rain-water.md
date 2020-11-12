# [42](https://leetcode.com/problems/trapping-rain-water/). Trapping Rain Water

Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.

``` python
# n  heights  -> how much trapping rain water
# list(int)   -> int
I: [0,1,0,2,1,0,1,3,2,1,2,1]
O: 6
```

clarification:

* n == height.length

## Ideas

### S1: DP + two pointers

* Find the **highest bar** first and keep track of the shorter one from both side. 
	* If the new bar > the current bar, we update it.
	* Otherwise, we count the difference as water.



### S2: Stack


## Exmaple

### S1: DP + two pointers

``` python 
                     |
          |💧💧💧💧 |
|💧💧💧💧|💧💧💧💧 |
```

## Code 


### DP + two pointer (v0.1

``` python
# Time: O(n) n = len(height)
# Space: O(1)

class Solution:
    def trap(self, height: List[int]) -> int:
        if len(height) <= 1: return 0
        highest = max(height)
        mark = height.index(highest)
        return self.cal(height[:mark]) + self.cal(height[mark:][::-1])
    
    def cal(self, nums):
        bar = 0
        water = 0
        for num in nums:
            water += max(0, bar - num)
            bar = max(num, bar)
        return water 
```

### version 0.2 Stack 

inspired by [Adeath](https://leetcode.com/problems/trapping-rain-water/discuss/17414/A-stack-based-solution-for-reference-inspired-by-Histogram)

The main idea is : 

- if we want to find out how much water on a `bar(bot)`, we need to find out the left larger bar's index (il), and right larger bar's index(ir), so that the water is `(min(A[il],A[ir])-A[bot])*(ir-il-1)`, use min since **only the lower boundary can hold water**, and we also need to handle the edge case that there is no il.
- To implement this we use **a stack that store the indices with decreasing bar height**, once we find a bar who's height is larger, then let the top of the stack be bot, the cur bar is `ir`, and the previous bar is `il`.

inspired by [solution](https://leetcode.com/problems/trapping-rain-water/solution/)

- we can use stack to keep track of the bars that are bounded by longer bars and hence, may store water. 
- **Using the stack**, we can do the calculations **in only one iteration**.
- We keep a stack and iterate over the array. 
	- We add the index of the bar to the stack if bar is smaller than or equal to the bar at top of stack, which means that the current bar is bounded by the previous bar in the stack. 
	- If we found a bar longer than that at the top, we are sure that the bar at the top of the stack is bounded by the current bar and a previous bar in the stack, hence, we can pop it and add resulting trapped water to ans.


``` python
Time: O(n)
Space: O(n)

class Solution:
    def trap(self, height: List[int]) -> int:
        stack, water = [], 0
        for right, bar in enumerate(height):
            print(stack)
            while stack and height[stack[-1]] < bar:
                top = stack.pop()
                if not stack: 
                    break
                left = stack.pop()
                distance = right - left - 1
                bounded_height = min(height[left], bar) - height[top]
                water += bounded_height * distance 
            stack.append(right)
        return water 
```

## Test

```
[2,1,0,2]
```
