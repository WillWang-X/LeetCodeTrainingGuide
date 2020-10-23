
<h1 align="center">
<br>
  <img src="https://i.imgur.com/mWp1gdR.gif" alt="Array" width=42%">
  <br><br>
Array
  <br><br>
</h1>

# Array 

![quick sort](https://i.imgur.com/mWp1gdR.gif)

## 基础知识

source: [elements](https://www.amazon.com/Elements-Programming-Interviews-Java-Insiders/dp/1517671272)

Array problems often have simple brute-force solutions that use 0(n) space, but subtler solutions that **use the array itself** to **reduce space** complexity to 0(1).


Front -> Back:

* Filling an array **from the front** is slow, so see if it's possible to **write values from the back**. 
* Instead of deleting an entry (which requires moving all entries to its right), consider **overwriting** it. When dealing with integers encoded by an array consider **processing the digits from the back** of the array. 
* Alternately, reverse the array so the **least-significant digit** is the first entry.

Be comfortable with writing code that operates on **subarrays**. 

It's incredibly easy to make **off-by-1** errors when operating on arrays. 

Don't worry about preserving the **integrity** of the array (sortedness, keeping equal entries together, etc.) until it is time to return. 

An array can serve as a good data structure when you know the distribution of the elements in advance. For example, a Boolean array of length W is a good choice for representing **a subset of** (0,1,..., W- 1]. (When using a Boolean array to represent a subset of (1,2,3,...,«}, allocate an array of size n+1 to simplify indexing.) 

When operating on 2D arrays, **use parallel logic** for rows and for columns. 

Sometimes it's easier to **simulate the specification**, than to analytically solve for the result. For example, rather than writing a formula for the i-th entry in the spiral order for an n X n matrix, just compute the output from the beginning. 

### Key word 

*  reduce space 
*  overwriting 
*  front to back (write or process)
*  used as hashmap
*  simulate the specification

## 典型应用

- **target**:
	- 1 unsorted -> quick select, [215](https://leetcode.com/problems/kth-largest-element-in-an-array/)
	- 1 sorted -> binary search, [35](https://leetcode.com/problems/search-insert-position/), [33](https://leetcode.com/problems/search-in-rotated-sorted-array/)
	- 2 sorted array -> dcrease & conquer, [4](https://leetcode.com/problems/median-of-two-sorted-arrays/)
	- N sorted array -> merge sort, [23](https://leetcode.com/problems/merge-k-sorted-lists/)
	- ⚃ sorted matrix  -> dcrease & conquer, [378](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)
- **pair** (x subarray):
	- dp (min_so_far), [121](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
	- x complement: [653](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/), [1049](https://leetcode.com/problems/last-stone-weight-ii/)
	- x subarray: [1031](https://leetcode.com/problems/maximum-sum-of-two-non-overlapping-subarrays/)
- **subarray**: 
	- sum: cumulative (prefix_sum), [325](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/)
	- two pointer, [209](https://leetcode.com/problems/minimum-size-subarray-sum/)
	- sliding window, [992](https://leetcode.com/problems/subarrays-with-k-different-integers/)
- **subsequence**: (duplicate, end with)
	- stack? 
	- dfs, [491](https://leetcode.com/problems/increasing-subsequences/)
	- dp, [300](https://leetcode.com/problems/longest-increasing-subsequence/)
	- greedy, [659](https://leetcode.com/problems/split-array-into-consecutive-subsequences/)

## 最佳实践

- [libraries]((https://i.imgur.com/VNGOnCx.png))
- preprocess: 
	- sort the array first -> binary search 
	- hashing (val -> index) 
	- a prefix/suffix sum/product -> to get subarray sum
- search 
	- sliding window / two pointers
	- use **index** instead of slicing when possible (O(1) vs O(n))
	- out of bounds
	- array used as a hashmap
- access / change
	- processing the element from the back
	- simulate

### corner case 

- Empty sequence.
- Sequence with 1 or 2 elements.
- Sequence with repeated elements.

### out of bounds

``` python
def is_in(x, y, matrix):
	return 0 <= x < len(matrix) and 0 <= y < len(matrix[0])
```

### prefix sum (subarry sum)

``` python
for i in range(1, len(nums)):
    nums[i] += A[i-1]
```

### caculate all pairs

``` python
def max_profit(prices: List[int]) -> int:
    maxprofit = 0
    if len(prices) <= 1:
        return 0
    minprice = prices[0]
    for i in range(1, len(prices)):
        maxprofit = max(prices[i] - minprice, maxprofit)
        minprice = min(prices[i], minprice)
    return maxprofit 
```

More general case: subarray and caculation involved. 

```  python
# all possible two subarray sum for i < j  (L < M)
# keep track of max(L) before a fixed `M`
          L(M)
         --
      -- 
   --
--
0, 1, 2, 3, 4, 5, 6, 7, 8, 9
		    ----
			  M(L)
```

``` python
left = 0
res = 0 
for i in range(1, len(nums)):
	left = max(left, cacluate_left(i))
	res = max(left + nums[i], res)
``` 

- Pracetice: [121](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/), [1031](https://leetcode.com/problems/maximum-sum-of-two-non-overlapping-subarrays/), 1041  


## 木桩训练

- [26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)
- [31. Next Permutation](https://leetcode.com/problems/next-permutation/description/)
- [36. Valid Sudoku](https://leetcode.com/problems/valid-sudoku/description/) 
- [48. Rotate Image](https://leetcode.com/problems/rotate-image/description/)
- [54. Spiral Matrix](https://leetcode.com/problems/spiral-matrix/description/)
- [55. Jump Game](https://leetcode.com/problems/jump-game/description/)
- [75. Sort Colors](https://leetcode.com/problems/sort-colors/description/)
- [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)
- [122. Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/)
- [204. Count Primes](https://leetcode.com/problems/count-primes/description/)



## Explain

## Q&A

## Thanks