# Generic Programming

> From 《冒号课堂》 3.1 泛型范式——抽象你的算法

## 问题

> “你们会不会经常遇到这样的情景：一遍又一遍地写着相似的代码，有心将其归并，却因种种原因无法践行。”

来看一下这些问题：

1. 从一个整数数组中随机抽取十个数，对其中的素数求和。
2. 将一个无序整数集中所有的完全平方数换成其平方根。
3. 从学生成绩表中，列出门门都及格且平均分在70分以上的学生名单。
4. 在一个着色二元树中，将所有的红色结点涂成蓝色。
5. 将一个字符串从倒数第3个字符开始反向拷贝到另一个字符串中。
6. 每从标准输入读取一个非数字的字符X，于标准输出打印“X不是数字字符”。

“请问它们之间有何共同之处？能否共享同一段代码？”

## 解决

> Generic Programming最著名的代表是C++中的STL（Standard Template Library）

``` c++
template <class Iterator, class Act, class Test> 
void process(Iterator begin, Iterator end, Act act, Test test) 

// 对容器中在给定范围内（即起于begin止于end）所有满足给定条件的元 
//素（即test（元素）==true）进行处理（即act（元素）） 
{ for ( ; begin != end; ++begin) // 从头至尾遍历容器内元素 
	// 若当前元素满足条件，则对其采取行动 
	if (test(*begin)) act(*begin); 
}
```

For exmaple, 题6


``` c++
#include <iostream> 
#include “process.h” // 前述process所在的头文件 

using namespace std; 

// 判断字符是否为非数字字符 
bool notDigit(char c) 
{ 
	return (c < '0') || (c > '9'); 
} 
	
// 打印非数字字符 
void printNondigit(char c)
{ 
	cout << c << "不是数字字符" << endl; 
} 

int main() 
{    
    process(istream_iterator<char>(cin),istream_iterator<char>(),printNondigit, notDigit); 
	return 0; 
}
```

## 效果 

Generic Programming，其基本思想是：将算法与其作用的数据结构分离，并将后者尽可能泛化，最大限度地实现算法重用。

这种泛化是基于模板（template）的参数多态（parametric polymorphism），相比OOP基于继承（inheritance）的子类型多态（subtyping polymorphism），不仅普适性更强，而且效率也更高。这不能不说是一种异数——我们知道，普适性往往是以效率为代价的。如果一定要找出代价的话，那就是其用法稍微复杂一些，可读性稍微差一些。


总结

* ➢ **泛型编程**能打破静态类型语言的数据类型之间的壁垒，在不牺牲效率并确保类型安全的情况下，最大限度地提高**算法的普适性**。
* ➢ STL有3要素：算法、容器和和迭代器。算法是一系列可行的步骤；容器是数据的集合，是抽象化的数组；**迭代器**是算法与容器之间的接口，是**抽象化的指针**。算法串联数据，数据实化算法。
* ➢ 泛型编程不仅能泛化算法中涉及的**概念**（数据类型），还能泛化**行为**（函数、方法、运算）。
* ➢ 泛型编程是算法导向的，以算法为中心，逐渐将其所涉及的**概念内涵模糊化**、**外延扩大化**，并将其所涉及的**运算抽象化、一般化**，从而提高算法的可重用性。
