<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/String-searching_algorithm">
  <img src="https://i.imgur.com/5dFnxJZ.png" alt="string" width=42%">
  </a>
  <br><br>
String
  <br><br>
</h1>


## 📝1. Basics

Similar to arrays, string problems often have simple brute-force solutions that use O(n) space solution, but subtler solutions that use the string itself to **reduce space** **complexity**.

Understand the implications of a string type which is **immutable**, e.g., the need to allocate a new string when concatenating immutable strings. Know alternatives to immutable strings, e.g., an array of characters or a `StringBuilder` in Java.

Updating a mutable string from the front is slow, so see if it's possible to **write values from the back**.

## ⚔️2. Use cases

1. **anagram**: sort, hashmap or counter 
2. **palindrome**: a == a[::-1] 
3. **substring**: counter, sliding window
4. **match**: 
	- KMP? 
	- Rabin Karp? 
	- wildcards, [10](https://leetcode.com/problems/regular-expression-matching/)
5. **search**: trie, [212](https://leetcode.com/problems/word-search-ii/)

## 🤺3. Best Practices

- counter 
- trie 
- suffix tree
- Rabin Karp
- [KMP](http://whocouldthat.be/visualizing-string-matching/)

### counter

``` python
# counter instead of hashmap for `a-z`
counter = [0 for _ in range(26)]
for c in letters:
	counter[ord(c)-ord('a')] += 1

# Space complexity is O(1) instead O(n). 
# Cause there  the upper bound is the range of characters, 
# which is usually a fixed constant of 26. 
```
### trie 

``` python
# simple trie used for preprocess
trie = {}
words= ['apple', 'banana', 'cherry']

cur = trie
for word in words:
	for c in word:
		if c not in cur: cur[c] = {}
		cur = cur[c]
```
or simpler 

``` python
_trie = lambda : collections.defaultdict(_trie)
```

``` python
def words_trie(words):
	trie = _trie()
	for _, word in enumerate(words):
		functools.reduce(dict.__getitem__, word, trie)["#"] = None 
```

### KMP(dive deep)

``` python
def kmp_matcher(pattern, text):
    pi = compute_prefix_function(pattern)
    matched = 0
    for i in range(len(text)):
        while matched > 0 and pattern[matched] != text[i]:
            matched = pi[matched - 1]
        if pattern[matched] == text[i]:
            matched += 1
        if matched == len(pattern):
            return i + 1 - len(pattern)
    return -1

def compute_prefix_function(pattern):
    pi = [0] * len(pattern)
    matched = 0
    for i in range(1, len(pattern)):
        while matched > 0 and pattern[i] != pattern[matched]:
            matched = pi[matched - 1]
        if pattern[i] == pattern[matched]:
            matched += 1
        pi[i] = matched
    return pi
```

## 😈4. More training

- [6. ZigZag Conversion](https://leetcode.com/problems/zigzag-conversion/)
- [12. Integer to Roman](https://leetcode.com/problems/integer-to-roman/)
- [67. Add Binary](https://leetcode.com/problems/add-binary/)


## 💬5. Explanation

- [The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets (No Excuses!)
](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/?from=groupmessage&isappinstalled=0): It does not make sense to have a string without knowing what encoding it uses. 


## ⚠️6. FAQs

#### Q: What are common string processing algorithms?

A: Some [categories](https://www.wikiwand.com/en/String_(computer_science)#/String_processing_algorithms) of algorithms include:

* String searching algorithms for finding a given substring or pattern
* String **manipulation** algorithms
* Sorting algorithms
* Regular expression algorithms
* Parsing a string
* Sequence mining