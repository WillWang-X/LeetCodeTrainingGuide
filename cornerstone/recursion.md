
<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Recursion">
  <img src="https://i.imgur.com/SAyEmMY.gif" alt="recursion" width=42%">
  </a>
  <br><br>
Recursion 
  <br><br>
</h1>


## 📝1. Basics

### 递归需要满足的三个条件

以“电影院询问自己是第几排？”为例。

1. 一个问题的解可以分解为几个**子问题**的解:  
	- “自己在哪一排”的问题，可以分解为“前一排的人在哪一排”这样一个数据规模更小的子问题。
2. 这个问题与分解之后的子问题，除了数据规模不同，**求解思路完全一样**:
	- 比如电影院那个例子，你求解“自己在哪一排”的思路，和前面一排人求解“自己在哪一排”的思路，是一模一样的。 
3. 存在**递归终止**条件: e.g. f(1) = 1

``` python 
def which_row(n):
	if n == 1: return 1
	return which_row(n-1) + 1

```

### 优点

代码的表达力很强，写起来简洁。

### 注意点

1.递归代码要警惕**堆栈溢出**

比如电影院的例子，如果我们将系统栈或者 JVM 堆栈大小设置为 1KB，在求解 f(19999) 时便会出现如下堆栈报错：
> Exception in thread "main" java.lang.StackOverflowError

解决：我们可以通过在代码中限制递归调用的最大深度的方式来解决这个问题。递归调用超过一定深度（比如 1000）之后，我们就不继续往下再递归了，直接返回报错。

``` python 
depth = 0 
def f(n):
	depth += 1
	if depth > 1000: 
		raise ValueError('depth > 1000')
	if n == 1: return 1
	return f(n-1) + 1
 
```
但这种做法并不能完全解决问题，因为最大允许的递归深度跟**当前线程剩余的栈空间大小有关，事先无法计算**。如果实时计算，代码过于复杂，就会影响代码的可读性。所以，如果最大深度比较小，比如 10、50，就可以用这种方法，否则这种方法并不是很实用。

2.递归代码要警惕**重复计算**

![fibonacci nummber](https://i.imgur.com/XkrEK8A.png)

``` python
# 1, 1, 2, 3, 5, 8, 13, 21
def fibonacci(n):
	if n == 1 or 2: return 1
	return fibonacci(n-1) + fibonacci(n-2)
```

从图中，我们可以直观地看到，想要计算 f(5)，需要先计算 f(4) 和 f(3)，而计算 f(4) 还需要计算 f(3)，因此，f(3) 就被计算了很多次，这就是重复计算问题。

为了避免重复计算，我们可以通过一个数据结构（比如hashmap）来保存已经求解过的 f(k)。

``` python 
# 1, 1, 2, 3, 5, 8, 13, 21
solved_map = {}
def fibonacci(n):
	if n == 1 or 2: return 1
	
	if n in solved_map:
		return solved_map[n]
	res = fibonacci(n-1) + fibonacci(n-2)
	solved[n] = res 
	
	return res 
```

3.递归代码要警惕**函数调用开销**

在时间效率上，递归代码里多了很多函数调用，当**这些函数调用的数量较大**时，就会积聚成一个可观的**时间成本**。

在空间复杂度上，因为递归调用一次就会在内存栈中保存一次现场数据，所以在分析递归代码空间复杂度时，需要额外考虑这部分的开销，比如我们前面讲到的电影院递归代码，空间复杂度并不是 O(1)，而是 O(n)。

解决：将**递归**写成**迭代**的方式。

``` python 
# 1  2  3  4  5  6 ...
# 1, 1, 2, 3, 5, 8, 13, 21
def fibonacci(n):
	if n == 1 or 2: return 1
	res = 0 
	pre = 0
	pre_pre = 0
	for i in range(3, n+1):
		res = pre + pre+pre
		prepre = pre
		pre = res 
	return res 
```

## ⚔️2. Use cases

* 推荐注册返佣金找到“最终推荐人”
* 电影院询问自己是第几排？去的过程叫“**递**”，回来的过程叫“**归**”

## 🤺3. Best Practices

## 😈4. More training

* [894. All Possible Full Binary Trees](https://leetcode.com/problems/all-possible-full-binary-trees/)

## 💬5. Explanation 

## ⚠️6. FAQs

#### Q: 是不是所有的递归代码都可以改为这种迭代循环的非递归写法呢？

A: 笼统地讲，是的。因为递归本身就是借助栈来实现的，只不过我们使用的栈是系统或者虚拟机本身提供的，我们没有感知罢了。如果我们自己在内存堆上实现栈，手动模拟入栈、出栈过程，这样任何递归代码都可以改写成看上去不是递归代码的样子。

但是这种思路实际上是将递归改为了“手动”递归，本质并没有变，而且也并没有解决前面讲到的某些问题，徒增了实现的复杂度。

#### Q: 我们平时调试代码喜欢使用 IDE 的单步跟踪功能，像规模比较大、递归层次很深的递归代码，几乎无法使用这种调试方式。对于递归代码，你有什么好的调试方法呢？

A: 调试递归:

1. 打印日志发现，递归值。
2. 结合条件断点进行调试。

#### Q: 如何理解递归的执行过程？

对于递归代码，若试图想清楚整个递和归的过程，实际上是进入了一个**思维误区**。

那该如何理解递归代码呢？**如果一个问题A可以分解为若干个子问题B、C、D，你可以假设子问题B、C、D已经解决。**而且，你只需要思考问题A与子问题B、C、D两层之间的关系即可，不需要一层层往下思考子问题与子子问题，子子问题与子子子问题之间的关系。屏蔽掉递归细节，这样子理解起来就简单多了。

因此，理解递归代码，就把它抽象成一个递推公式，不用想一层层的调用关系，不要试图用人脑去分解递归的每个步骤。

#### Q: Recursion vs Iteration?

source: [geeksforgeeks](https://www.geeksforgeeks.org/difference-between-recursion-and-iteration/) - Read More

A: 

* **Time Complexity**: Finding the Time complexity of Recursion is more difficult than that of Iteration.
* **Usage**: Usage of either of these techniques is a trade-off between time complexity and size of code. If time complexity is the point of focus, and number of recursive calls would be large, it is better to use iteration. However, if time complexity is not an issue and shortness of code is, recursion would be the way to go.
* **Overhead**: Recursion has a large amount of Overhead as compared to Iteration.
* **Infinite Repetition**: Infinite Repetition in recursion can lead to CPU crash but in iteration, it will stop when memory is exhausted.





