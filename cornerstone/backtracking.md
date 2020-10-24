<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Backtracking">
  <img src="https://i.imgur.com/2Y3D3fI.gif" alt="Backtracking" width=42%">
  </a>
  <br><br>
Backtracking
  <br><br>
</h1>


## 📝1. Basics

**Backtracking** is a general algorithm for finding all (or some) solutions to some computational problems, notably constraint satisfaction problems, that incrementally builds candidates to the solutions, and abandons a candidate ("backtracks") as soon as it determines that the candidate cannot possibly be completed to a valid solution.[1][2]


## ⚔️2. Use cases

- subset
- permutation 
- combination sum
- palindrome partitioning

## 🤺3. Best Practices

### path: permutation(visited)
``` python
# remove `nums`, `res` if you write a nested function
def backtrack(path, nums, res):
	# base case 
	if len(path) == len(nums):
		res.append(path)
	# general case 
	for num in set(nums) - set(path):
		backtrack(path+[num], nums, res)
	return res 
```

- simulate instead of passing a new list 

``` python
# use one to simulate `push`, `pop` instead of passing a new list.\
# more effective 

class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        res = []
        def backtrack(path):
            if len(path) == len(nums):
                res.append(path[:])
            for num in set(nums) - set(path):
                path.append(num)
                backtrack(path)
                path.pop()
            return res 
        return backtrack([])
```
- use index instead of passing a list 
 
``` python
def permute(self, nums):

    def backtrack(start, end):
        if start == end:
            ans.append(nums[:])
        for i in range(start, end):
            nums[start], nums[i] = nums[i], nums[start]
            backtrack(start+1, end)
            nums[start], nums[i] = nums[i], nums[start]
            
    ans = []
    backtrack(0, len(nums))
    return ans
```


### path: subset(order)

``` python 
# 1, 2, 3 

	       []
		/   |  \
	   1   2    3
	  / \   \
	 2   3   3    
 	 |
     3 
```


``` python 
# remove `nums`, `res` if you write a nested function
def backtrack(path, i, nums, res):
	# base case 
	res.append(path)
	# general case 
	for nxt in range(i, len(nums)):
		backtrack(path + [nums[nxt]], nxt+1, nums, res)
	return res 
```

- Try: [78](https://leetcode.com/problems/subsets/)

### path: combination sum(early stop)

``` python 
# with duplicate 
def backtrack(path, i, target, res, nums):
	# backtracking 
	if target < 0:
		return 
	# base case 
	if target == 0:
		res.append(path)
	# general case 
	for nxt in range(i, len(nums)):
		backtrack(path+[nums[nxt]], nxt, target-nums[nxt], res, nums)
	return res 
```

### path: palindrome partitioning(condition)

``` python 
def backtrack(path, i, res, s):
	# base case 
	if i == len(s):
		res.append(path)
	# general case 
	for nxt in range(i, len(s)):
		# condition
		if is_palindrome(i, nxt):
			backtrack(path + [s[i:nxt+1]], nxt+1, res, s)
```

## 😈4. More training

* [31. Next Permutation](https://leetcode.com/problems/next-permutation/)
* [39. Combination Sum](https://leetcode.com/problems/combination-sum/)
* [40. Combination Sum II](https://leetcode.com/problems/combination-sum-ii/)
* [46. Permutations](https://leetcode.com/problems/permutations/)
* [47. Permutations II](https://leetcode.com/problems/permutations-ii/)
* [60. Permutation Sequence](https://leetcode.com/problems/permutation-sequence/)
* [78. Subsets](https://leetcode.com/problems/subsets/)
* [90. Subsets II](https://leetcode.com/problems/subsets-ii/)
* [131. Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/)
* [266. Palindrome Permutation](https://leetcode.com/problems/palindrome-permutation/)
* [267. Palindrome Permutation II](https://leetcode.com/problems/palindrome-permutation-ii/)

## 💬5. Explanation

## ⚠️6. FAQs