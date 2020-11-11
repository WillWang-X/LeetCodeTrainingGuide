# [146](https://leetcode.com/problems/lru-cache/). LRU Cache

## Ideas
 
* First in, First out
* Delete (key, val) & check capacity before `put()`
* Move (key, val) to the end before `get()`

## Code 

### [v](https://github.githistory.xyz/willwang-x/algorithms-2018/blob/master/problems/leetcode/146.md)0.1 

``` python 
class LRUCache:

    def __init__(self, capacity: int):
        self.cache = collections.OrderedDict()
        self.capacity = capacity

    def get(self, key: int) -> int:
        if key not in self.cache: return -1 
        self.cache.move_to_end(key)
        return self.cache[key]
        
    def put(self, key: int, value: int) -> None:
        if key in self.cache: del self.cache[key] # test1
        if len(self.cache) >= self.capacity: 
            self.cache.popitem(last=False)
        self.cache[key] = value
```

## Tests

### Test 1 

```
["LRUCache","get","put","get","put","put","get","get"]
[[2],[2],[2,6],[1],[1,5],[1,2],[1],[2]]
```