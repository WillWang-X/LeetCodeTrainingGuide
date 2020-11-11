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


``` python
b _____ b 
↑       ↑
i       j     

if s[i] == s[j] and is_palindrome(s[i+1:j]):
	longest = j - i + 1
	res = s[i:j+1]

-----------

   x x x x x 
x  \
x    \
x      \ 
x        \
x          \

```

## Example

``` python
# string -> the longest palindromic substring
# string -> string
I: "babad"
O: "aba"
```

``` python
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

class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        def palindrome(left, right):
            while left - 1 >= 0 and right + 1 < len(s) and s[left-1] == s[right+1]:
                left -= 1
                right += 1
            len_ = right - left + 1
            res = s[left:right+1]
            return len_, res 

        
        longest = 0
        pa_res = ""
        for i, char in enumerate(s):
            test = [(i, i)]
            if i + 1 < len(s) and s[i+1] == char:
                test.append((i, i+1))
                
            for left, right in test:
                len_, pa = palindrome(left, right)
                if len_ > longest:
                    longest = len_
                    pa_res = pa
        return pa_res 
```

### v0.2 DP 

``` python
# Time: O(N*N)
# Space: O(N*N)

class Solution:
    def longestPalindrome(self, s: str) -> str:
        
        if not s:
            return ""
        
        longest = 1
        palindromic = s[0]
        result = [ ["False" for i in range(len(s))] for j in range(len(s)) ]
        for i in range(len(s)):
            result[i][i] = "True"

        for i in range(len(s)-1):
            if s[i] == s[i+1]:
                result[i][i+1] = "True"
                longest = 2
                palindromic = s[i:i+2]
        
        for i in range(len(s)-2,-1,-1):
            for j in range(i+2,len(s)):
                if s[i] == s[j] and result[i+1][j-1] == "True":
                    result[i][j] = "True"
                    if j-i+1 > longest:
                        longest = j-i+1
                        palindromic = s[i:j+1]
                    print("{:<1} {:<1} {:<6} {:<6}".format(i, j, s[i:j+1], result[i][j]), "b/c-of", s[i+1:j])
                else:
                    print("{:<1} {:<1} {:<6} {:<6}".format(i, j, s[i:j+1], result[i][j]))
                  
        print("-"*10)
        for i in range(len(result)):
            # for j in range(i, len(result)):
            print(["{:<1} {:<1} {:<6} {:<5}".format(i, j, s[i:j+1], result[i][j]) for j in range(len(result))] )
                # print(s[i:j+1], result[i][j])
        return palindromic 
```

## Test