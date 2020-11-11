# [5](https://leetcode.com/problems/longest-palindromic-substring/). Longest Palindromic Substring

## Ideas

### Brute force

* check each pair (i, i), (i, i+1) 
* to find the longest palindromic that centers on those pairs.

``` python
_______ x _______
   <- L   R -> 

        or

_______ xx _______
   <- L    R -> 
```

### DP, O(n^2)

We define P(i, j) = 

* true, if the substring S<sub>i</sub> ... S<sub>j</sub> is palindrome
* false,​ otherwise
  	
Therefore:

P(i, j) = (P(i+1, j-1) and S<sub>i</sub> = S<sub>j</sub>) 

The base cases are: 

* P(i, i) = true
* P(i, i+1) = (S<sub>i</sub> = S<sub>i+1</sub>)


## Example

``` python
# string -> the longest palindromic substring
# string -> string
I: "babad"
O: "aba"
```

``` python
# ababa -> ababa
# i, j, string, boolean, reason
2 4 aba    True   b/c-of b
1 3 bab    True   b/c-of a
1 4 baba   False 
0 2 aba    True   b/c-of b
0 3 abab   False 
0 4 ababa  True   b/c-of bab
----------
['0 0 a      True ', '0 1 ab     False', '0 2 aba    True ', '0 3 abab   False', '0 4 ababa  True ']
['1 0        False', '1 1 b      True ', '1 2 ba     False', '1 3 bab    True ', '1 4 baba   False']
['2 0        False', '2 1        False', '2 2 a      True ', '2 3 ab     False', '2 4 aba    True ']
['3 0        False', '3 1        False', '3 2        False', '3 3 b      True ', '3 4 ba     False']
['4 0        False', '4 1        False', '4 2        False', '4 3        False', '4 4 a      True ']
```

## Code 


### v0.1 Brute Force

``` python
# Time: O(n^2) where n = len(s)
# Space: O(n)

class Solution:
    def __init__(self):
        self.longest = 0
        self.res_pal = ""
    
    def longestPalindrome(self, s: str) -> str:
        for i in range(len(s)):               
            for left, right in self._cases(i, s):
                length, palindrome = self._palindrome(left, right, s)
                self._update(length, palindrome)
        return self.res_pal 
    
    def _cases(self, i, s):
        cases = [(i, i)]
        if i + 1 < len(s) and s[i+1] == s[i]:
            cases.append((i, i+1))
        return cases
    
    def _palindrome(self, left, right, s):
        while left - 1 >= 0 and right + 1 < len(s) and s[left-1] == s[right+1]:
            left -= 1
            right += 1
        len_ = right - left + 1
        res = s[left:right+1]
        return len_, res 
    
    def _update(self, length, palindrome):
        if length > self.longest:
            self.longest = length
            self.res_pal = palindrome
```

### v0.2 DP 

``` python
# Time: O(N*N)
# Space: O(N*N)

class Solution:
    def __init__(self):
        self.result = []
        self.longest = 0
        self.palindromic = "" 
    
    def longestPalindrome(self, s: str) -> str:
        if not s: return ""
        self._preprocess(s)
        
        for i in range(len(s)-2,-1,-1):
            for j in range(i+2,len(s)):
                if s[i] == s[j] and self.result[i+1][j-1] == True:
                    self.result[i][j] = True
                    self._update(i, j, s) 
        return self.palindromic 
    
    def _update(self, i, j, s):
        if j-i+1 > self.longest:
            self.longest = j-i+1
            self.palindromic = s[i:j+1]     

    def _preprocess(self, s):
        self.palindromic = s[0]
        self.longest = 0
        self.result = [ [False for i in range(len(s))] for j in range(len(s))]
        
        for i in range(len(s)):
            self.result[i][i] = True
        
        for i in range(len(s)-1):
            if s[i] == s[i+1]:
                self.result[i][i+1] = True
                self.longest = 2
                self.palindromic = s[i:i+2]
```

## Test

```
"aaaa" -> "aaaa"
```