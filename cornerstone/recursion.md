
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

source: elements

Recursion is especially suitable when **the input is expressed using recursive rules** such as a computer grammar.

Recursion is a good choice for **search, enumeration, and divide-and-conquer**.

Use recursion as **alternative to deeply nested iteration** loops. For example, recursion is much better when you have an undefined number of levels, such as the IP address problem generalized to k substrings.

If you are asked to **remove recursion** from a program, consider mimicking call stack with the **stack data structure**.

Recursion can be easily removed from a **tail-recursive** program by using a while-loop—no stack is needed. (Optimizing compilers do this.)

If a recursive function may end up being called with the **same arguments** more than once, **cache** the results—this is the idea behind Dynamic Programming (Chapter 13).

## ⚔️2. Use cases

* 推荐注册返佣金找到“最终推荐人”
* 电影院询问自己是第几排？去的过程叫“**递**”，回来的过程叫“**归**”

## 🤺3. Best Practices

``` python
def which_row(n):
	if n == 1: return 1
	return which_row(n-1) + 1
```

## 😈4. More training

* [894. All Possible Full Binary Trees](https://leetcode.com/problems/all-possible-full-binary-trees/)

## 💬5. Explanation 

递归要满足三个条件：

以“电影院询问自己是第几排？”为例。

1. 可分解为子问题的解：
	- “自己在哪一排”的问题，可以分解为“前一排的人在哪一排”这样一个数据规模更小的子问题。
2. 子问题，**求解思路完全一样**:
	- 比如电影院那个例子，你求解“自己在哪一排”的思路，和前面一排人求解“自己在哪一排”的思路，是一模一样的。 
3. 存在**递归终止**条件: e.g. f(1) = 1

``` python 
def which_row(n):
	if n == 1: return 1
	return which_row(n-1) + 1
```


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


#### Q: What are pitfalls when using recursion?

A: Here are 3:

1. 递归代码要警惕**堆栈溢出**
1. 递归代码要警惕**重复计算**
1. 递归代码要警惕**函数调用开销**
