# [218](https://leetcode.com/problems/the-skyline-problem/). The Skyline Problem

## Problem

Given the locations and height of all the [buildings](https://i.imgur.com/hn3ScjA.png), write a program to output the [skyline](https://i.imgur.com/gywyDNu.png) formed by these buildings collectively.

``` python
# list([Li,  Ri,  Hi ]) -> list([Xi,  Yi ])
# list([int, int, int]) -> list([int, int])
I: [[2,9,10],[3,7,15],[5,12,12],[15,20,10],[19,24,8]]
O: [[2,10],[3,15],[7,12],[12,0],[15,10],[20,8],[24,0]]
```

* **Skyline**: A city's skyline is the outer contour of the silhouette formed by all the buildings in that city when viewed from a distance.
* **key points**: A key point is the left endpoint of a horizontal line segment. A list of "key points" (red dots in Figure B) in the format of [ [x1,y1], [x2, y2], [x3, y3], ... ] uniquely defines a skyline. 

## Ideas

### 1. Identify the change

``` python 
[ [2 9 10], [3 7 15], [5 12 12], [15 20 10], [19 24 8] ] 
[2, 10], [9, 10], [3, 15], [7, 15], [5, 12], ...
 2,       9,       3,       7,       5....  
 # Q: To check if they can be a critical point
 # A: When a height changed
```

* Iterate all point.x 
* Check if the height where point stays at changed, which need a way to get the height of the current situation   

``` python 
def get_skyline(self, buildings):
	points = preprocess(buildings)
	live = [(height, end_x)] # heap to get the highest one
	res = []
	for x, height, end_x in points:
		remove_dead_from_live(live, x)
		add_new_to_live(live, height, end_x)
		if changed(live.first, res): 
			res.append([x, height])
	return res
```

### 2. sweep line algorithm 

```
   *------->
    *-------->
*------>
                   *----->
                       *------>
```

* Sorted Q by `y`: to add all events `*------->`
* Faced with enter event: 
	* Add critical point if event.y > Q.highest
	* add event to Q 
* Faced with leave event:
	* Add critical point if event is the highest
	* remove event from Q

## Example 

``` python
"""
I: [[2,9,10],[3,7,15],[5,12,12],[15,20,10],[19,24,8]] 
O: [[2,10],[3,15],[7,12],[12,0],[15,10],[20,8],[24,0]]
"""
----------
points:  [(0, -1)] # x, y
active:  [(0, inf)] # active-y, end_x
----------
x    y     end_x , [active-y, active_x]          
----------------------------------------
##  0
2    -10   9     , [(0, inf)]                    
2    -10   9     , [(-10, 9), (0, inf)]          
----------
cause :  active_height-y 10  != last_point_height-y -1  
points:  [(0, -1), [2, 10]]
--------------------
##  1
3    -15   7     , [(-10, 9), (0, inf)]          
3    -15   7     , [(-15, 7), (0, inf), (-10, 9)]
----------
cause :  active_height-y 15  != last_point_height-y 10  
points:  [(0, -1), [2, 10], [3, 15]]
--------------------
##  2
5    -12   12    , [(-15, 7), (0, inf), (-10, 9)]
5    -12   12    , [(-15, 7), (-12, 12), (-10, 9), (0, inf)]
----------
cause :  active_height-y 15  == last_point_height-y 15  
points are still the same
--------------------
##  3
7    0     0     , [(-15, 7), (-12, 12), (-10, 9), (0, inf)]
7    0     0     , [(-12, 12), (0, inf), (-10, 9)]
----------
cause :  active_height-y 12  != last_point_height-y 15  
points:  [(0, -1), [2, 10], [3, 15], [7, 12]]
--------------------
##  4
9    0     0     , [(-12, 12), (0, inf), (-10, 9)]
9    0     0     , [(-12, 12), (0, inf), (-10, 9)]
----------
cause :  active_height-y 12  == last_point_height-y 12  
points are still the same
--------------------
##  5
12   0     0     , [(-12, 12), (0, inf), (-10, 9)]
12   0     0     , [(0, inf)]                    
----------
cause :  active_height-y 0   != last_point_height-y 12  
points:  [(0, -1), [2, 10], [3, 15], [7, 12], [12, 0]]
--------------------
##  6
15   -10   20    , [(0, inf)]                    
15   -10   20    , [(-10, 20), (0, inf)]         
----------
cause :  active_height-y 10  != last_point_height-y 0   
points:  [(0, -1), [2, 10], [3, 15], [7, 12], [12, 0], [15, 10]]
--------------------
##  7
19   -8    24    , [(-10, 20), (0, inf)]         
19   -8    24    , [(-10, 20), (0, inf), (-8, 24)]
----------
cause :  active_height-y 10  == last_point_height-y 10  
points are still the same
--------------------
##  8
20   0     0     , [(-10, 20), (0, inf), (-8, 24)]
20   0     0     , [(-8, 24), (0, inf)]          
----------
cause :  active_height-y 8   != last_point_height-y 10  
points:  [(0, -1), [2, 10], [3, 15], [7, 12], [12, 0], [15, 10], [20, 8]]
--------------------
##  9
24   0     0     , [(-8, 24), (0, inf)]          
24   0     0     , [(0, inf)]                    
----------
cause :  active_height-y 0   != last_point_height-y 8   
points:  [(0, -1), [2, 10], [3, 15], [7, 12], [12, 0], [15, 10], [20, 8], [24, 0]]
--------------------
```

## Code 

### v0.7

``` python
class Solution:
    def getSkyline(self, buildings: List[List[int]]) -> List[List[int]]:
        events = self._preprocess(buildings)
        active = [(0, float('inf'))]  # -y, end_x
        points = [(0, -1)]            #  x, y
        
        for x, y, end_x in events:
            while self._expired(active[0][1], x):
                heapq.heappop(active)
            if self._is_height(y): 
                heapq.heappush(active, (y, end_x))
            if self._changed(active[0][0], points[-1][-1]):
                points.append([x, -active[0][0]])
        return points[1:]
    
    def _changed(self, active_height, last_height):
        return -active_height != last_height
    
    def _preprocess(self, buildings):
        left = [(l,-h,r) for l,r,h in buildings]
        right = list(set([(r,0,0) for _,r,_ in buildings]))
        return sorted(left + right)
    
    def _is_height(self, height):
        return height < 0
    
    def _expired(self, active_x, cur_x):
        return active_x <= cur_x     
```

### sweep line algorithm v0.2

``` python
from collections import namedtuple
from bisect import insort, bisect_left

class Solution:
    
    def __init__(self):
        self.Event = namedtuple('Event', ('y', 'x', 'id', 'type'))
        self.enter = 0
        self.leave = 1

    def getSkyline(self, buildings: List[List[int]]) -> List[List[int]]:
        events = self._preprocess(buildings)
        active = [self.Event(0, -1, None, self.enter)]
        points = {}

        for e in sorted(events, key=lambda e: e.x):
            if e.type == self.enter:
                if e.y > active[-1].y: 
                    points[e.x] = e.y
                insort(active, e)
            else:
                if self._is_highest(e, active[-1]): 
                    points[e.x] = active[-2].y
                active.pop(bisect_left(active, events[e.id]))
                
        return [[x, points[x]] for x in sorted(points.keys())]
    
    def _preprocess(self, buildings):
        events = [self.Event(Hi, Li, i, 0) for i, (Li, Ri, Hi) in enumerate(buildings)] + [
                  self.Event(Hi, Ri, i, 1) for i, (Li, Ri, Hi) in enumerate(buildings)]
        return events
    
    def _is_highest(self, e1, e2):
        return e1.y == e2.y and e1.id == e2.id
```

## Test

### test 1

```
[[0,2,3],[2,5,3]]
```

## More 

* [The skyline problem](https://briangordon.github.io/2014/08/the-skyline-problem.html)