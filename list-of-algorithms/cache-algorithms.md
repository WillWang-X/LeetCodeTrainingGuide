# Cache algorithms: Cache replacement policies

> choose which items to discard to make room for the new ones. [[wiki](https://www.wikiwand.com/en/Cache_replacement_policies)]

## Why 

* Space is limited you have to choose one to discard when the cache is full.
* 优先级算法可以参考这个

## How

1. Bélády's algorithm
1. First in first out (FIFO)
1. Last in first out (LIFO) or First in last out (FILO)
1. **Least recently used (LRU)**: Discards the least recently used items first.
1. Time aware least recently used (TLRU)
1. Most recently used (MRU)
1. Pseudo-LRU (PLRU)
1. Random replacement (RR)
1. Segmented LRU (SLRU)
1. Least-frequently used (LFU)
1. Least frequent recently used (LFRU)
1. LFU with dynamic aging (LFUDA)
1. Low inter-reference recency set (LIRS)
1. CLOCK-Pro
1. Adaptive replacement cache (ARC)
1. AdaptiveClimb (AC)
1. Clock with adaptive replacement (CAR)
1. Multi queue (MQ)
1. Pannier: Container-based caching algorithm for compound objects

## What