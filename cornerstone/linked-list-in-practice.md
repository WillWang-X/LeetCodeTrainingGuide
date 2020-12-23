<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/List_of_data_structures">
  <img src="https://i.imgur.com/iCUdnOe.png" alt="data structure from wiki" width=42%">
  </a>
  <br><br>
Linked list
  <br><br>
</h1>


> In computer science, a linked list is a linear collection of data elements whose order is not given by their physical placement in memory. Instead, each element points to the next. It is a data structure consisting of a collection of nodes which together represent a sequence. In its most basic form, each node contains: **data**, and a **reference** (in other words, a link) to the next node in the sequence. [[wiki](https://www.wikiwand.com/en/Linked_list)]

## 📝1. Basics

List problems often have a simple brute-force solution that uses 0(n) space, but a subtler solution that uses **the existing list nodes** to reduce space complexity to 0(1). 

Very often, a problem on lists is conceptually simple, and is more about **cleanly coding what's specified**, rather than designing an algorithm.

Consider using **a dummy head** (sometimes referred to as a sentinel) to avoid having to check for empty lists. This simplifies code, and makes bugs less likely. 

It's easy to forget **to update next** (and previous for double linked list) for the head and tail.

Algorithms operating on singly linked lists often benefit from using **two iterators**, one ahead of the other, or **one advancing quicker than the other**. 
 
## ⚔️2. Use cases

- `+`: dummy node: [2](https://leetcode.com/problems/add-two-numbers/description/)
- `-`: delete in O(1): moditfy the value or pointer 
- `%`: fast & slow 
	- **kth**: get the kth from last node 
	- **middle**: get the middle node 
	- **cycle**: detect cycle 
- `*`: 
	- reverse 1 or K: [25](https://leetcode.com/problems/reverse-nodes-in-k-group/description/), [92](https://leetcode.com/problems/reverse-linked-list-ii/description/), [206](https://leetcode.com/problems/reverse-linked-list/description/)
	- merge 2 or K

## 🤺3. Best Practices


#### [node class](https://repl.it/@WillWang42/linked-list) 

``` python 
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
```

#### add (double)

``` python 
# ... <-> p <-> tail
# ... <-> p <-> node <-> tail
def _add(node):
	p = tail.prev
	p.next, node.prev = node, p
	node.next, tail.prev = tail, node
```

#### dummy node

``` python
def xxxx(self, l1: ListNode, l2: ListNode) -> ListNode:
	dummy = cur = ListNode()
	# do sth. with cur
	return dummy.next 
```

#### delete 

``` python
# to delete a node (except the tail) in a singly linked list, 
# given only access to that node.
# node -> next -> next.next 
# next ---------> next.next
def delete_node(self, node):
    node.val  = node.next.val
    node.next = node.next.next
```

#### delete (double)

``` python
# pre_node <-> node <-> nxt_node
# pre_node <-> nxt_node
def delete(node):
	pre_node, nxt_node = node.pre, node.nxt
	pre_node.nxt, nxt_node.pre = nxt_node, pre_node
```

#### kth(back)

``` python
def remove_Nth_from_end(head: ListNode, n: int) -> ListNode:
    fast = slow = head
    for _ in range(n):
        fast = fast.next
    if not fast:
        return head.next
    while fast.next:
        fast = fast.next
        slow = slow.next
    slow.next = slow.next.next
    return head
```
 
#### middle

``` python
def middle_node(self, head: ListNode) -> ListNode:
    slow = fast = head
    while fast and fast.next:
        slow = slow.next 
        fast = fast.next.next 
    return slow
```

#### cycle 

``` python
def has_cycle(head):
    fast, slow = head, head 
    while fast and fast.next:
        fast, slow = fast.next.next, slow.next 
        if fast == slow:  
            return True 
    return False 
```

#### [reverse](https://leetcode.com/problems/reverse-linked-list/description/) 

``` python
"""
   pre | cur -> cur.nxt 
   x <-  pre |  cur 
"""	
def reverse_node(head):
	pre, cur = None, head
	while cur:
		cur.next, pre, cur = pre, cur, cur.next 
	return pre
```

#### merge

``` python
def merge_two(l1: ListNode, l2: ListNode) -> ListNode:
    if l1 and l2:
        if l1.val > l2.val: 
            l1, l2 = l2, l1 
        l1.next = merge_two(l1.next, l2)
    return l1 or l2 
```

#### merge k 

#### merge sort 

``` python
# merge sort
def sort_list(self, head):
    """
    :type head: ListNode
    :rtype: ListNode
    """
    # base case 
    if not head or not head.next:
        return head

    # divide list into two parts
    fast, slow = head.next, head
    while fast and fast.next:
        fast = fast.next.next
        slow = slow.next
    second = slow.next
    slow.next = None

    l = self.sort_list(head)
    r = self.sort_list(second)
    return self.merge_two(l, r)
``` 

## 😈4. More training

* [2](https://leetcode.com/problems/add-two-numbers/). Add Two Numbers
* [117](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/).
* 146.
* [147](https://leetcode.com/problems/insertion-sort-list/description/).
* 450.
* [25](https://leetcode.com/problems/reverse-nodes-in-k-group/). Reverse Nodes in k-Group



## 💬5. Explanation

## ⚠️6. FAQs
 
##### Q: What are common corner cases considered in the linked list  problems?

A: Here are 4 I think of: 

* None.
* Single node.
* Two nodes.
* Linked list has cycle.