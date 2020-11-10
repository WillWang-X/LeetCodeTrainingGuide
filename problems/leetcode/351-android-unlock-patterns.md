# [351](https://leetcode.com/problems/android-unlock-patterns/). Android Unlock Patterns


## Idea

Backtracking: 

* **Base base**: the condition we get result 
* **End base**: the condition we end the exploration
* **Explore**: remember visited and define the node's valid neighbor

## Example 

* 1 <= m, n <= 9

``` python
# m,   n   -> number of unique and valid unlock patterns
# int, int -> int
# 1,   3   -> 385

# visited, nxt_num, length
set() 1 1
{1} 2 2
{1, 2} 3 3
{1, 2} 4 3
{1, 2} 5 3
{1, 2} 6 3
{1, 2} 7 3
{1, 2} 9 3
{1} 4 2
{1, 4} 2 3
{1, 4} 3 3
{1, 4} 5 3
{1, 4} 7 3
{1, 4} 8 3
{1, 4} 9 3
{1} 5 2
{1, 5} 2 3
{1, 5} 3 3
{1, 5} 4 3
{1, 5} 6 3
{1, 5} 7 3
{1, 5} 8 3
{1, 5} 9 3
```

## Code 

### V0.2

``` python
class Solution:
        
    def __init__(self):
        self.nums = [i for i in range(1, 10)]
        self.has_obstacle = self._get_obstacle()
        self.count = 0 
        self.least = 0
        self.most = 0
        
    def numberOfPatterns(self, m: int, n: int) -> int:
        self.least, self.most = m, n
        for num in self.nums:
            self.visited = set()
            self._get_patterns(num, 1)        
        return self.count 
    
    def _get_patterns(self, num, length):
        if self._base_case(length): self.count += 1
        if self._end_case(length): return 
        
        self.visited.add(num)
        for nxt in self._valid_neighbor(num):
            self._get_patterns(nxt, length+1)
        self.visited.remove(num)
        
    def _valid_neighbor(self, num):
        for nxt in self.nums:
            if nxt not in self.visited: 
                if (num, nxt) in self.has_obstacle and self.has_obstacle[(num, nxt)] not in self.visited: continue
                yield nxt
        
    def _base_case(self, length):
        return self.least <= length <= self.most
    
    def _end_case(self, length):
        return length == self.most
        
    def _get_obstacle(self):
        a = {(1,3):2, (1,7):4, (1,9):5}
        b = {(2,8):5}
        c = {(3,1):2, (3,7):5, (3,9):6}
        d = {(4,6):5}
        
        f = {(6,4):5}
        g = {(7,1):4, (7,3):5, (7,9):8}
        h = {(8,2):5}
        i = {(9,1):5, (9,3):6, (9,7):8}
        return {**a, **b, **c, **d, **f, **g, **h, **i}
```

## Test 

``` python
1, 1 -> 9
1, 3 -> 385
4, 9 -> 389112
9, 9 -> 140704
1, 9 -> 389497
```