# [1239](https://leetcode.com/problems/maximum-length-of-a-concatenated-string-with-unique-characters/). Maximum Length of a Concatenated String with Unique Characters

## Ideas 

``` python
DP[i+1] = arr[i+1] | (each in DP[i])
```

* The new combination is from arr[i+1] with each in combinations


## Example 

```
I: arr = ["un","iq","ue"]
O: 4
```

``` python
# arr[i],  dp[i]
{}         [set()]
{'n', 'u'} [set(), {'n', 'u'}]
{'q', 'i'} [set(), {'n', 'u'}, {'q', 'i'}, {'q', 'n', 'u', 'i'}]
{'u', 'e'} [set(), {'n', 'u'}, {'q', 'i'}, {'q', 'n', 'u', 'i'}, {'u', 'e'}, {'q', 'i', 'u', 'e'}]
```

## Code 

### v0.1

``` python
class Solution:
    def maxLength(self, arr: List[str]) -> int:
        dp = [set()]
        for a in arr:
            if not self.is_unique(a): continue 
            a = set(a)
            for b in dp[:]:
                if self.is_overlap(a, b): continue
                dp.append(self.combine(a, b))
        return max(len(x) for x in dp)
    
    def is_unique(self, a):
        return len(set(a)) == len(a)
    
    def is_overlap(self, a, b):
        return a & b
    
    def combine(self, a, b):
        return a | b
```

## Test 

```
["yy","bkhwmpbiisbldzknpm"]
["ab","cd","cde","cdef","efg","fgh","abxyz"]
```
