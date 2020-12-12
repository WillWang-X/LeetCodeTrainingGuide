<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Brute-force_search">
  <img src="https://i.imgur.com/vcmxEGk.gif" alt="intuitive image" width=42%">
  </a>
  <br><br>
Brute-force search 
  <br><br>
</h1>

> In computer science, brute-force search or **exhaustive search**, also known as **generate and test**, is a very general problem-solving technique and **algorithmic paradigm** that consists of **systematically** enumerating all possible **candidates** for the solution and checking whether each candidate **satisfies** the problem's statement. [[wiki](https://www.wikiwand.com/en/Brute-force_search)]

## Why 

While a brute-force search is simple to implement, and will always find a solution if it exists, its cost is proportional to the number of candidate solutions – which in many practical problems tends to grow very quickly as the size of the problem increases. Therefore, brute-force search is typically used when 

* **the problem size is limited**, or when 
* there are problem-specific **heuristics** that can be used to reduce the set of candidate solutions to **a manageable size**. The method is also used when 
* the **simplicity** of implementation is more important than speed.

This is the case, for example, in critical applications where any errors in the algorithm would have very serious consequences; or when using a computer to prove a mathematical theorem. Brute-force search is also useful as **a baseline method** when benchmarking other algorithms or metaheuristics. Indeed, brute-force search can be viewed as the simplest **metaheuristic**. Brute force search should not be confused with backtracking, where large sets of solutions can be discarded without being explicitly enumerated (as in the textbook computer solution to the eight queens problem above). The brute-force method for finding an item in a table – namely, check all entries of the latter, sequentially – is called **linear search**.

## How
  
``` python
c ← first(P)
while c ≠ Λ do
    if valid(P,c) then
        output(P, c)
    c ← next(P, c)
end while
```

* c: the solution
* P: the instance 
* Λ: a "null candidate", some conventional data value 


For example, when looking for the divisors of an integer n, the instance data P is the number n. 

* The call `first(n)` should return **the integer 1** if n ≥ 1, or Λ otherwise; 
* the call `next(n,c)` should return **c + 1** if c < n, and Λ otherwise; and 
* `valid(n,c)` should return **true** if and only if c is a divisor of n. (In fact, if we choose Λ to be n + 1, the tests n ≥ 1 and c < n are unnecessary.)

The brute-force search algorithm above will call output for every candidate that is a solution to the given instance P. The algorithm is easily modified to stop after finding the first solution, or a specified number of solutions; or after testing a specified number of candidates, or after spending a given amount of CPU time.



## What 

### Overview

In computer science, brute-force search or **exhaustive search**, also known as **generate and test**, is a very general problem-solving technique and **algorithmic paradigm** that consists of **systematically** enumerating all possible **candidates** for the solution and checking whether each candidate **satisfies** the problem's statement.

### Exmaples

* A brute-force algorithm to find the **divisors** of a natural number n would enumerate all integers from 1 to n, and check whether each of them divides n without remainder. 
* A brute-force approach for the **eight queens puzzle** would examine all possible arrangements of 8 pieces on the 64-square chessboard, and, for each arrangement, check whether each (queen) piece can attack any other.


### Others

* Implementing the brute-force search
* Combinatorial explosion
* Speeding up brute-force searches
* Reordering the search space
* Alternatives to brute-force search
* In cryptography


## FAQs

#### Q: brute-force search vs backtracking?

A: Brute force search should not be confused with backtracking, where large sets of solutions can be discarded without being **explicitly enumerated** (as in the textbook computer solution to the eight queens problem above).


