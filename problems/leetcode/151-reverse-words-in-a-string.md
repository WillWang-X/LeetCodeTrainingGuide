# [151](https://leetcode.com/problems/reverse-words-in-a-string/). Reverse Words in a String


## Ideas

* split -> reverse -> join

## Code 

### v0.1

``` python
class Solution:
    def reverseWords(self, s: str) -> str:
        return " ".join(s.strip().split()[::-1])
``` 

