<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Stack_(abstract_data_type)">
  <img src="https://i.imgur.com/O6tbQ6f.png" alt="stack" width=42%">
  </a>
  <br><br>
Stack
  <br><br>
</h1>

> when to pop and push?
> 
> **Stack** is a linear data structure which follows **a particular order** in which the operations are performed. The order may be LIFO(Last In First Out) or FILO(First In Last Out). [[wiki](https://www.wikiwand.com/en/Stack_(abstract_data_type))]

## 📝1. Basics

Learn to recognize when the stack **LIFO** property is applicable. For example, **parsing** typically benefits from a stack. 

Consider augmenting the basic stack or queue data structure to support additional operations, such as **finding the maximum element**. 

## ⚔️2. Use cases


- LIFO: [901](https://leetcode.com/problems/online-stock-span/) [how]
- **save for later**: parsing, [394](https://leetcode.com/problems/decode-string/)  [why]
- **special order**: discrete ascending or descending, [84](https://leetcode.com/problems/largest-rectangle-in-histogram/) [what]
- **next greater**: [496](https://leetcode.com/problems/next-greater-element-i/)  [when]
- top-down (DFS-style): tree, [173](https://leetcode.com/problems/binary-search-tree-iterator/)  [who]

## 🤺3. Best Practices

#### general (DFS style)

``` python 
# to maintain an order in the stack (= save for later)
# e.g. LC1019, nearest largest 
for i, num in enumerate(input):
	# base case 
	while stack and compare(num, stack[-1]):
		# hit the bottom 
		last = stack.pop()
		# caculate...
	# general case 
	stack.append(i)
```

#### dummy value (nearest largest) 

``` python
def largest_rectangle_area(self, heights: List[int]) -> int:
    heights.append(0)             # dummy value 
    stack = [(float("-inf"), -1)] # dummy value: val, pos 
    ans = 0
    for i, num in enumerate(heights):
        while num < stack[-1][0]: # no while stack and ...
            h = stack.pop()[0]
            w = i - stack[-1][1] - 1
            ans = max(ans, h * w)
        stack.append((num, i))
    return ans
```

#### save for later 

``` python
def decode_string(self, s: str) -> str:
    stack = []
    for i, char in enumerate(s):
        if char == "]":
            letters = ""
            while stack and stack[-1] != "[":
                letters = stack.pop() + letters
            stack.pop() # pop "["
            digits = ""
            while stack and stack[-1].isdigit():
                digits = stack.pop() + digits 
            stack.append(int(digits) * letters)
        else:
            stack.append(char)
    return "".join(stack)
```

```
s = "3[a]2[bc]", return "aaabcbc".
s = "3[a2[c]]", return "accaccacc".
s = "2[abc]3[cd]ef", return "abcabccdcdcdef".
s = "10[a]", return "aaaaaaaaaa".
```

## 😈4. More training

* [155. Min Stack](https://leetcode.com/problems/min-stack/) 🌟
* [84.Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/) 42, 84, 85, 221, 801, 739, 901, 907, 1019 (7 solved in 1 way)
* [907.Sum of Subarray Minimums](https://leetcode.com/problems/sum-of-subarray-minimums/) 
* [94.Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/description/) (Iterative, 系列)!  pre-order, 394 🌟
* [232.Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)
* [770.Basic Calculator IV](https://leetcode.com/problems/basic-calculator-iv/) (系列)
* [42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/) 🌟
* [496. Next Greater Element I 系列](https://leetcode.com/problems/next-greater-element-i/) 🌟 

## 💬5. Explanation

* [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
	* It is the same as the question that just have one kind of bracket. We use a hashmap to store the relationship between open and close brackets. Now, hashmap is an abstraction of **brackets** relationship.
	* **Push** the present character into stack if it's an opening symbol else **pop** a character from stack and **check** if it matches with the present character ( if it matches don't do anything else immediately return `false` )
	* **Note** * At any point of time if stack is empty and present character is a closing bracket return `false` immediately
	* **Termination** * if stack is empty return `true` else return `false`	

## ⚠️6. FAQs

##### Q: stack 和 heap 有什么区别？

A: 

- 都在维持某种顺序，而stack通过pop()和push()完成，而heap需要进入容器之后二次处理得到。
- Stack: Last in, First out -> When pop? -> Discrete Order (需要照顾原始数组Index)
- Heap: Last in, Best out (定制化能力更强)
- Queue: First in, First out

##### Q: stack的优化有什么？
 
A: 如果不关注过程，只在乎结果。可以使用变量`count`来标记，空间由`O(n)`到`O(1)`, 如[LC 1021](https://leetcode.com/problems/remove-outermost-parentheses/), 请试着用stack和count分别解决。是不是有一种在DP中，二维cache压缩成一维的感觉。
