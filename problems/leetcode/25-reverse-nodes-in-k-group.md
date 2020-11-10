#  [25](https://leetcode.com/problems/reverse-nodes-in-k-group/). Reverse Nodes in k-Group

## Ideas

do its part and recursively to reverse the rest part

* **edge case**: if `k` < 2   
* **base case**: if we have k nodes
* **reverse**: reverse k nodes 
* **recursion**: reverseKgroup for the rest part

``` python
head    |
 1 -> 2 -> 3 -> ...

do reverse ( 1 -> 2 )  
head.nxt = reverseKGroup(3 -> ...)
return pre # (2 -> 1 -> ....)
```

## Exmaple 

``` python
# ListNode, int -> ListNode
I: [1,2,3,4,5] 2
O: [2,1,4,3,5]
```

``` python 
1 -> 2 -> 3 -> 4 -> 5
2 -> 1 -> ()
2 -> 1 -> 4 -> 3 -> ()
2 -> 1 -> 4 -> 3 -> 5 
```

## Code 

### v0.7

``` python
class Solution:
    def reverseKGroup(self, head: ListNode, k: int) -> ListNode:
        # 1. edge case 
        if k < 2: return head
        
        # 2. base case: check if we have k node
        node = head
        for _ in range(k):
            if not node: return head
            node = node.next
            
        # 3. reverse 
        pre, cur = None, head
        for _ in range(k):
            cur.next, pre, cur = pre, cur, cur.next 
        
        # 4. recursion 
        head.next = self.reverseKGroup(cur, k)
        
        return pre
```

## Test 

``` python
[1,2], 2      -> [2,1]
[1,2,3], 2    -> [2,1,3]
[1,2,3,4], 2  -> [2,1,4,3]
```
