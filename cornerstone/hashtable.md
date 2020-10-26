<h1 align="center">
<br>
	<a href="https://just-taking-a-ride.com/inside_python_dict/chapter2.html">
  <img src="https://i.imgur.com/l1598o9.gif" alt="data structure from wiki" width=42%">
  </a>
  <br><br>
Hash Table
  <br><br>
</h1>

> In computing, a hash table (hash map) is a data structure that implements an **associative array abstract data type**, a structure that can map **keys** to **values**. [[wiki](https://www.wikiwand.com/en/Hash_table)]

## 📝1. Basics

source: Elements

Hash tables have **the best theoretical and real-world performance** for lookup, insert and delete. Each of these operations has O(1) time complexity. The O(1) time complexity for insertion is for the average case—a single insert can take O(n) if the hash table has to be resized.

Consider using a hash code as a **signature** to enhance performance, e.g., to filter out candidates. 

Consider using a precomputed lookup table instead of boilerplate if-then code for mappings,
e.g., from character to value, or character to character.

When defining your own type that will be put in a hash table, be sure you understand the relationship between **logical equality** and the fields the hash function must inspect. Specifically, anytime equality is implemented, it is imperative that the correct hash function is also implemented, otherwise when objects are placed in hash tables, logically equivalent objects may appear in different buckets, leading to lookups returning false, even when the searched item is present.

Sometimes you’ll need a **multimap**, i.e., a map that contains multiple values for a single key, or a bi-directional map. If the language’s standard libraries do not provide the functionality you need, learn how to implement a multimap using lists as values, or find **a third party library** that has a multimap.

- deal with exception
- collision 
- hash function
- open hashing or closed hashing
- loading factor

## ⚔️2. Use cases

* cache: [523](https://leetcode.com/problems/continuous-subarray-sum/description/)

## 🤺3. Best Practices

- prefix sum
- lowercase hashmap
- design a hashmap
- LRU: hashmap + linkedlist

### prefix sum

``` python 
def max_subarray_len(nums: List[int], k: int) -> int:
    prefix_sum = {0: -1} # sum_ : index
    sum_ ,size = 0, 0
    for i, num in enumerate(nums):
        sum_ += num
        if sum_ - k in prefix_sum:
            size = max(size, i - prefix_sum[sum_ - k])
        if sum_ not in prefix_sum:
            prefix_sum[sum_] = i 
    return size
```

### lowercase hashmap

``` python 
def group_anagrams(self, strs: List[str]) -> List[List[str]]:
    ans = collections.defaultdict(list)
    for s in strs:
        count = [0] * 26
        for c in s:
            count[ord(c) - ord('a')] += 1
        ans[tuple(count)].append(s)
    return list(ans.values())
```

## 😈4. More training

* 1 Two Sum
* 18 4Sum 
* 36 Valid Sudoku
* 49 Group Anagrams 
* 136 Single Number
* [138 Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/): hashmap x linkedlist 
* 149 Max Points on a Line 
* 166 Fraction to Recurring Decimal 
* 170 Two Sum III * Data structure design 
* 204 Count Primes 
* 217 Contains Duplicate 
* 325 Maximum Size Subarray Sum Equals k (类型)
* 350 Intersection of Two Arrays II 
* 454 4Sum II 
* 535 Encode and Decode TinyURL

## 💬5. Explanation

* **Advantages**: The main advantage of hash tables over other table data structures is speed. This advantage is more apparent when the number of entries is **large**. Hash tables are particularly efficient when the maximum number of entries can be predicted in advance, so that the bucket array can be allocated once with the optimum size and never resized.
* **Drawbacks**: Although operations on a hash table take constant time on average, the cost of a good hash function can be significantly higher than the inner loop of the lookup algorithm for a sequential list or search tree. Thus hash tables are **not effective** when the number of entries is very **small**. (However, in some cases the high cost of computing the hash function can be mitigated by saving the hash value together with the key.)



## ⚠️6. FAQs

**Q: 如何设计一个工业级水平的散列表？**

A: 

* 要点：
	* **能用**：增，删，查
	* **资源少**
	* **性能稳定**：特殊情况表现正常，e.g. 扩容
* 方案：
	* 散列函数：
		* 散列值随机且均匀分布
		* hash function简单：直接寻址法、平方取中法、折叠法、随机数法
	* 装载因子阈值&动态扩容策略
		* 内存多求效率，则降低loading factor
		* 分批扩容 
	* 散列冲突解决方法  
		* 链表法更加普适, 因为链表对**内存**利用比开放寻址高，因为需要才创建，而不需要提前申请空间。另外，链表法中的链表可以被修改为**动态查找数据结构**，比如红黑树、跳表，来避免散列表时间复杂度退化成O(n)，抵御散列冲突攻击, 如 Java 中 LinkedHashMap。
		* 小规模数据、装载因子小时，使用open hashing。 如 Java中的ThreadLocalMap。

e.g. 小型例子：[instant-runoff voting](https://repl.it/@WillWang42/instant-runoff-voting)	

**Q: How to design a good hash algorithm?**

A: 

* **单向**哈希： 从哈希值不能反向推导出哈希值。
* **篡改**无效： 对输入敏感，哪怕原始数据只修改一个Bit，最后得到的哈希值也大不相同。
* 散列**冲突**： 散列冲突的概率要很小，对于不同的原始数据，哈希值相同的概率非常小。
* 执行**效率**： 哈希算法的执行效率要尽量高效，针对较长的文本，也能快速计算哈希值。

**Q: 哈希算法的常见应用有哪些？**

A: 7个常见应用如下：

1. 安全加密： MD5, SHA, DES, AES. Trade-off 在于破解难度和计算时间，e.g. [防脱库](https://www.wired.com/story/facebook-passwords-plaintext-change-yours/)
2. 唯一标识：如更快的搜图，取图的前100个字节，后100...hash完，作为唯一标识。
3. 数据校验：如BT下载确认文件的安全、正确、完整。
4. 散列函数：关注于散列后的值能不能平均分布，以及散列函数的执行快慢。
5. 负载均衡：取模运算，将同一个IP的请求，都路由到同一个后端服务器。
6. 数据分片：数据太多，统计“搜索关键词”，MapReduce思路。
7. 分布式存储：**一致性哈希算法**解决[雪崩效应](https://www.wikiwand.com/zh/%E9%9B%AA%E5%B4%A9%E6%95%88%E5%BA%94)。

**Q: [区块链](https://www.wikiwand.com/en/Blockchain)和哈希算法有什么关系？**

A: 区块链是一块块区块组成的，每个区块分为两部分：区块头和区块体。
区块头保存着 「自己区块体」 和 「上一个区块头」 的哈希值。因为这种链式关系和哈希值的唯一性，只要区块链上任意一个区块被修改过，后面所有区块保存的哈希值就不对了。区块链使用的是 SHA256 哈希算法，计算哈希值非常耗时，如果要篡改一个区块，就必须重新计算该区块后面所有的区块的哈希值，短时间内几乎不可能做到。