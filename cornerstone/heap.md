# Heap 


![max heap](https://i.imgur.com/LHCxZOp.gif)


## 基础知识 

Use a heap when all you care about is the **largest** or **smallest** elements, and you do not need to support fast lookup, delete, or search operations for arbitrary elements. [Problem 11.1]

A heap is a good choice when you need to compute the k **largest** or k **smallest** elements in a collection. For the former, use a min-heap, for the latter, use a max-heap. [Problem 11.4]

## 典型应用

- first in, best out 
- top / lowest k: [347](https://leetcode.com/problems/top-k-frequent-elements/description/)
- shortest path: [787]
- merge k lists

## 最佳实践

- min heap
- max heap
- shortest path + Dijkstra
- merge k sorted


### min heap: benchmark

``` python
import heapq
def find_kth_largest(nums: List[int], k: int) -> int:
    heap = []
    for num in nums:
        heapq.heappush(heap, num)
        if len(heap) > k:
            heapq.heappop(heap)
    return heap[0]

# Time: O(nlogk) where n = len(nums)    
```

### max heap: keep poping 

``` python
def find_kth_largest(self, nums: 'List[int]', k: 'int') -> 'int':
    heap = [-x for x in nums]
    heapq.heapify(heap)
    for i in range(k):
        result = heapq.heappop(heap)
    return -result 
    
# 	return heapq.nlargest(k, nums)[-1]    
# Time: O(n + klogn) where n = len(nums)
```

### k closest 

``` python
def k_closest(points: List[List[int]], K: int) -> List[List[int]]:
    return heapq.nsmallest(K, points, key = lambda x: x[0]*x[0] + x[1]*x[1])
```

- [973](https://leetcode.com/problems/k-closest-points-to-origin/)

### Dijkstra

``` python
def shortest(graph, start, dest):
	hq = [(0, start)]
	visited = set()
	while hq:
		cost, node = heapq.heappush(hq)
		# edge case 
		if node in visited: continue 
		# base case 
		if node == dest: return cost
		# general case 
		visited.add(node)
		for child, dist in graph[node]:
			heapq.heappush(hq, (cost+dist, child))
	return "Not found"
	
graph = {1: [[2, 10], [4, 20]]}	
```

### merge k sorted? 

``` python
1 -> 5 -> 8 -> 10
2 -> 9 -> 12
4 -> 7 -> 11

heap = [1, 2, 4] 
```


``` python
class tuplebyfirst(tuple):
    "tuple that sorts only on first element"
    def __lt__(self, other):
        return self[0] < other[0]   
```

``` python
def merge_K_lists(self, lists: List[ListNode]) -> ListNode:
    dummy = cur = ListNode(0)
    hq = [tuplebyfirst((n.val, n)) for n in lists if n]
    heapq.heapify(hq)
    
    while hq:
        v, n = heapq.heappop(hq)
        if n.next:
            heapq.heappush(hq, tuplebyfirst((n.next.val, n.next)))
        cur.next = n
        cur = cur.next 
    return dummy.next 
```

``` python
# heapq.merge(*data)
def merge_k_lists(self, lists: List[ListNode]) -> ListNode:
    def vals(node):
        while node:
            yield node.val
            node = node.next

    dummy = last = ListNode(None)
    for val in heapq.merge(*map(vals, lists)):
        last.next = last = ListNode(val)

    return dummy.next
```

## 木桩训练 

- [215. Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)
- [347. Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
- [295. Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)

## Explain

## Q&A

### 1. How many ways do we have to find k largest element? 

n = len(nums)

- sort:  `O(nlogn + 1)` sort and return `nums[-k]`
- min heap: `O(nlogk)` maintain a min heap of size of k and return `heaps[0]`
- max heap: `O(n + klogn)` heapify and pop k times
- quick select: `O(n)` 

## Thanks



