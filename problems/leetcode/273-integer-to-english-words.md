# [273](https://leetcode.com/problems/integer-to-english-words/). Integer to English Words

## Problem 

Convert a non-negative integer to its english words representation. Given input is guaranteed to be less than 231 - 1.

``` python
# non-negative integer -> english words representation
# int                  -> str
I: 123
O: "One Hundred Twenty Three"
```

Clarification:

* 0 <= num <= 2<sup>31</sup> - 1 (2,147,483,647) (~= 2*10<sup>9</sup>)


## Ideas

Decrease and conquer:

* Break down problems until we find it in our cache.

```
1,234,567,891
```

* thousand = 1,000
* million = 1,000,000
* billion = 1,000,000,000


## Example 

``` python
# 1234567891 -> "One Billion Two Hundred Thirty Four Million Five Hundred Sixty Seven Thousand Eight Hundred Ninety One"

Input: 1234567891
--------------------
 => Break 1234567891 down 1   Billion and 234567891
   1       ==> We got One   

Input: 234567891
--------------------
 => Break 234567891  down 234 Million and 567891
 ==> Break 234    down Two Hundred and 34    
 ==> Break 34     down Thirty and 4     
   4       ==> We got Four  

Input: 567891
--------------------
 => Break 567891     down 567 Thousand and 891   
 ==> Break 567    down Five Hundred and 67    
 ==> Break 67     down Sixty and 7     
   7       ==> We got Seven 
 ==> Break 891    down Eight Hundred and 91    
 ==> Break 91     down Ninety and 1     
   1       ==> We got One   
```

## Code 

### v 0.1


``` python
class Solution:
    def __init__(self):
        self.to19 = 'One Two Three Four Five Six Seven Eight Nine Ten Eleven Twelve ' \
           'Thirteen Fourteen Fifteen Sixteen Seventeen Eighteen Nineteen'.split()
        self.tens = 'Twenty Thirty Forty Fifty Sixty Seventy Eighty Ninety'.split()
        self.base = ['Thousand', 'Million', 'Billion']    
    
    def numberToWords(self, num: int) -> str:        
        return ' '.join(self.words(num)) or 'Zero'
    
    def words(self, n):
        if n == 0:    return []
        if n <  20:   return [self.to19[n-1]]
        if n <  100:  return [self.tens[n//10-2]]  + self.words(n%10)
        if n <  1000: return [self.to19[n//100-1]] + ['Hundred'] + self.words(n%100)

        for p, w in enumerate(self.base, 1):
            if n < 1000**(p+1):
                return self.words(n//1000**p) + [w] + self.words(n%1000**p)
``` 

## Test 

```
123
12345
1234567
1234567891
```
