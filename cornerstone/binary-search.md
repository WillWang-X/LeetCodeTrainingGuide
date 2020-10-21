
<h1 align="center">
<br>
  <img src="https://i.imgur.com/7Wh8Jm3.gif"Aogrithms with Illustration" width=42%">
  <br>
    <br>
Binary Search
</sup>  <br><br>
</h1>


## 📝1. Basics

Binary search is an efficient algorithm for finding an item from a **sorted** list of items. It works by repeatedly dividing in half the portion of the list that could contain the item, until you've narrowed down the possible locations to just one. 

Binary search is an effective search tool. It is **applicable** to more than just searching in **sorted** arrays, e.g., it can be used to search an **interval** of real numbers or integers.

If your solution uses sorting, and the **computation** performed after sorting is faster than sorting, e.g., O(n) or O(log n), look for 
solutions that do not perform a complete sort.

Consider **time/space tradeoffs**, such as making multiple passes through the data.


## ⚔️2. Use cases

* Search in sorted array: [35](https://leetcode.com/problems/search-insert-position/) 
* Identify the sorted part: [33](https://leetcode.com/problems/search-in-rotated-sorted-array/)

## 🤺3. Best Practices

### Search insert position

* x < `target` for x in nums[:**`i`**]<br><img src="https://i.imgur.com/uIf4WS9.png" alt="shortcuts" width="42%"/>

``` python
def get_insert_pos(nums: List[int], target: int) -> int:
    return bisect.bisect_left(nums, target)
```


## 😈4. More training


* [33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) 🌟
* [35. Search Insert Position](https://leetcode.com/problems/search-insert-position/) 👾
* [300. Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)👻
* [354. Russian Doll Envelopes](https://leetcode.com/problems/russian-doll-envelopes/)👹
* [81. Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)

## 💬5. Explanation 

* Given an arbitrary collection of n keys, the only way to determine if a search key is present is by examining each element. This has O(n) time complexity. Fundamentally, binary search is a **natural elimination-based strategy** for searching a **sorted** array. The idea is to eliminate half the keys from consideration by keeping the keys in sorted order. If the search key is not equal to the middle element of the array, one of the two sets of keys to the left and to the right of the middle element can be eliminated from further consideration.

## ⚠️6. FAQs 

**Q: Is there are API that do binary search without building wheels by yourself?**

A: [Python API: bisect](https://repl.it/@WillWang42/8-6-bisect)