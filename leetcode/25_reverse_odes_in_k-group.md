#  25. Reverse Nodes in k-Group


Given a linked list, reverse the nodes of a linked list k at a time and return its modified list.

k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes in the end should remain as it is.


```
Example:

Given this linked list: 1->2->3->4->5

For k = 2, you should return: 2->1->4->3->5

For k = 3, you should return: 3->2->1->4->5
```

Note:

* Only constant extra memory is allowed.
* You may not alter the values in the list's nodes, only nodes itself may be changed.

## Idea

- Edge case 
- Base case 
- Recursive

## Code 

### Version 1.0

``` python
"""

() -> (A - B - C) -> ()

()
C
C_next 
A
"""

# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def reverseKGroup(self, head, k):
        """
        :type head: ListNode
        :type k: int
        :rtype: ListNode
        """
        def reverse(head, tail):
            new_head = tail
            new_tail = head 
            
            prev = None 
            curr = head 
            for _ in range(k):
                temp = curr.next 
                curr.next = prev
                prev = curr 
                curr = temp
            
            return new_head, new_tail 
            
        
        dummy = ListNode("dummy")
        dummy.next = head
        
        pre_last = dummy 
        
        cur = dummy 
        count = 0
        while count < k and cur.next:
            cur = cur.next 
            count += 1
            if count == k:
                temp = cur.next 
                head, tail = reverse(pre_last.next, cur)
                pre_last.next = head 
                pre_last = tail 
                cur = tail
                cur.next = temp
                count = 0 
                
        return dummy.next 
```

## Version 2.0

``` python 
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def reverseKGroup(self, head, k):
        """
        :type head: ListNode
        :type k: int
        :rtype: ListNode
        """
        # 1. edge case  k = 1, len(sub) < k 
        if k < 2: return head 
        node = head 
        for _ in range(k):
            if not node:
                return head 
            node = node.next 
        
        # 2. reverse 
        cur = head 
        pre = None 
        for _ in range(k):
            temp = cur.next
            cur.next = pre
            pre = cur
            cur = temp
                
        # 3. recursive  1->2->3->4
        head.next = self.reverseKGroup(cur, k)
        return pre
```


