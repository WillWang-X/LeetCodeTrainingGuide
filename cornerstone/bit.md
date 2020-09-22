# Bit 

<img src="https://i.imgur.com/S6s8tb6.png" alt="bit" width="400"/>

> or, and, exculsive-or, not, <<, >>

## 基础知识

source: [wiki](https://www.wikiwand.com/en/Bit_manipulation)

Questions involving binary representations and bitwise operations are asked sometimes and you must be absolutely familiar with how to convert a number **from decimal form into binary form (and vice versa)** in your chosen programming language.

Bit manipulation is the act of algorithmically manipulating bits or other pieces of data shorter than a word. Computer programming tasks that require bit manipulation include **low-level device control**, **error detection** and **correction** algorithms, **data compression**, **encryption** algorithms, and **optimization**. For most other tasks, modern programming languages allow the programmer to work directly with abstractions instead of bits that represent those abstractions. Source code that does bit manipulation makes use of the bitwise operations: **AND**, **OR**, **XOR**, **NOT**, and **bit shifts**.

Bit manipulation, in some cases, can obviate or reduce the need to loop over a data structure and can give many-fold speed ups, as bit manipulations are processed in parallel, but the code can become more difficult to write and maintain.

## 典型应用

- XOR `^` (消消乐)
- Bit state

## 最佳实践

Some helpful utility snippets:

- `num |=  (1 << k)`: **Set** k<sup>th</sup> bit. e.g. (0 or 1) -> **1**
- `num &= ~(1 <<k)`: **Turn off** k<sup>th</sup> bit. e.g. (0, 1) -> **0**
- `num ^=  (1 << k)`: **Toggle** the k<sup>th</sup> bit. e.g. (0->1, 1-> 0)
- Check if k<sup>th</sup> bit is set: `num & (1 << k) != 0`. aka. 0 or 1?
- Check if A == 2<sup>?</sup>::: `A&(A-1) == 0`. e.g. 8(1000), 8-1 (111) -> 0000
- **Remove** last **1** bit: `A&(A-1)` e.g. num: xxx1000, num-1: xxx0111
- Get all 1-bits: `~0`

---

- base 10 to base 2 
- count `1`s by `A&(A-1)`
- get sum of a and b (& ^)
- missing number `^`
- bit states - `(1 << k) | state`, [847](https://leetcode.com/problems/shortest-path-visiting-all-nodes/)

### binary/hexadecimal to decimal

``` python
# binary/hexadecimal to decimal 
int('11', 2) # 3
int('F', 16) # 15 

# decimal to binary
bin(10)[2:] # '1010'
```
### count `1`s

``` python 
def ones_in_bin(num):
	count = 0
	while n:
		n = n&(n-1) # remove last one
		count += 1
	return count
```

### get sum of a and b 

``` python
def get_sum(a, b):
  if b == 0: return a 
  return get_sum(a^b, (a&b)<<1) # sum/remainder, carry/quotient
```

### missing number 

``` python
def missing_number(nums):
	res = len(nums)
	for i, num in enumerate(nums):
		res ^= i ^ num
	return res
```

- [more tricks @repl](https://repl.it/@WillWang42/bit-manipulation)

### bit states

``` python
def shortest_path_length(self, graph: List[List[int]]) -> int:
    N = len(graph)
    # bit state
    q = collections.deque(( 1 << x, x) for x in range(N))
    dist = collections.defaultdict(lambda: N*N)
    for x in range(N): dist[1 << x, x] = 0 
    
    while q:
        cover, head = q.popleft()
        d = dist[cover, head]
        if cover == 2**N - 1: return d
        for child in graph[head]:
        	# update bit state
            cover2 = cover | (1 << child) 
            if d + 1 < dist[cover2, child]:
                dist[cover2, child] = d + 1
                q.append((cover2, child))
```

- Try [847](https://leetcode.com/problems/shortest-path-visiting-all-nodes/)

### corner cases

* Check for overflow/underflow.
* Negative numbers.

## 木桩训练

- [260. Single Number III](https://leetcode.com/problems/single-number-iii/)
- [268. Missing Number](https://leetcode.com/problems/missing-number/)
- [371. Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/)
- [411. Minimum Unique Word Abbreviation](https://leetcode.com/problems/minimum-unique-word-abbreviation/)
- [1017. Convert to Base -2](https://leetcode.com/problems/convert-to-base-2/)

## Explain

- [268. Missing Number](https://leetcode.com/problems/missing-number/)
	- We can **harness the fact that XOR** is its own inverse to find the missing element in linear time.
	- Because we know that `nums` contains n numbers and that it is missing exactly one number on the range [0..n−1], we know that *n* definitely replaces the missing number in `nums`. Therefore, if we initialize an integer to n and XOR it with every index and value, we will be left with the missing number. 




## Q&A

## More 

- [handbooks](https://github.com/yangshun/tech-interview-handbook/tree/master/algorithms)
- [A summary: how to use bit manipulation to solve problems easily and efficiently](https://leetcode.com/problems/sum-of-two-integers/discuss/84278/A-summary%3A-how-to-use-bit-manipulation-to-solve-problems-easily-and-efficiently)