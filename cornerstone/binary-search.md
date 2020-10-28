
<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Binary_search_algorithm">
  <img src="https://i.imgur.com/7Wh8Jm3.gif" alt="binary search" width=42%">
  </a>
  <br><br>
Binary Search
  <br><br>
</h1>


## 📝1. Basics

Binary search is an efficient algorithm for finding an item from a **sorted** list of items. It works by repeatedly dividing in half the portion of the list that could contain the item, until you've narrowed down the possible locations to just one. 

Binary search is an effective search tool. It is **applicable** to more than just searching in **sorted** arrays, e.g., it can be used to search an **interval** of real numbers or integers.

If your solution uses sorting, and the **computation** performed after sorting is faster than sorting, e.g., O(n) or O(log n), look for 
solutions that do not perform a complete sort.

Consider **time/space tradeoffs**, such as making multiple passes through the data.


## ⚔️2. Use cases

* Search **answer**: [35](https://leetcode.com/problems/search-insert-position/) 
* Simple binary search: [74](https://leetcode.com/problems/search-a-2d-matrix/)
* Search step **simulation**: [50](https://leetcode.com/problems/powx-n/)
* Sort **modification**: [33](https://leetcode.com/problems/search-in-rotated-sorted-array/), [4](https://leetcode.com/problems/median-of-two-sorted-arrays/)

## 🤺3. Best Practices

#### Search insert position

* x < `target` for x in nums[:**`i`**]<br><img src="https://i.imgur.com/uIf4WS9.png" alt="shortcuts" width="42%"/>

``` python
def get_insert_pos(nums: List[int], target: int) -> int:
    return bisect.bisect_left(nums, target)
```

#### Get the [middle](https://repl.it/@WillWang42/get-the-middle) 

fast and safe way

``` python
def get_middle(left: int, right: int) -> int:
    return (left + right) >> 1
```

#### Sort 

Sometimes, we need define **sort** before binary search 

e.g. [[4,5], [4,7], [1,2]] -> [[1,2], [4,7], [4,5]]

``` python 
def sort(self, nums: List[List[int]]) -> nums: List[List[int]]:
    f = lambda x, y: x[0] - y[0] if x[0] != y[0] else y[1] - x[1]
    nums.sort(key = functools.cmp_to_key(f))
    return nums
```



## 😈4. More training


1. [33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) 🌟
1. [35. Search Insert Position](https://leetcode.com/problems/search-insert-position/) 👾
1. [300. Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)👻
1. [354. Russian Doll Envelopes](https://leetcode.com/problems/russian-doll-envelopes/)👹
1. [81. Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)

## 💬5. Explanation 

* Given an arbitrary collection of n keys, the only way to determine if a search key is present is by examining each element. This has O(n) time complexity. Fundamentally, binary search is a **natural elimination-based strategy** for searching a **sorted** array. The idea is to eliminate half the keys from consideration by keeping the keys in sorted order. If the search key is not equal to the middle element of the array, one of the two sets of keys to the left and to the right of the middle element can be eliminated from further consideration.

## ⚠️6. FAQs 

**Q: Is there are API that do binary search without building wheels by yourself?**

A: [Python API: bisect](https://repl.it/@WillWang42/8-6-bisect)

**Q: What are the pitfalls in implementing binary search?**

A: Here are some [I can think of](https://stackoverflow.com/questions/504335/what-are-the-pitfalls-in-implementing-binary-search):

* **Off-by-one errors**, when determining the boundary of the next interval
* **Handling of duplicate items**, if you are suppose to return the first equal item in the array but instead returned a subsequent equal item
* **Numerical underflows/overflows** when computing indices, with huge arrays
* **Recursive vs non-recursive implementation**, a design choice you should consider