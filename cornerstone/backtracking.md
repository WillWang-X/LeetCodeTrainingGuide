<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Backtracking">
  <img src="https://i.imgur.com/2Y3D3fI.gif" alt="Backtracking" width=42%">
  </a>
  <br><br>
Backtracking
  <br><br>
</h1>

> The backtracking algorithm enumerates a set of **partial candidates** that, in principle, could be **completed** in various ways to give all the possible solutions to the given problem. The completion is done **incrementally**, by a sequence of candidate extension steps.
 [[wiki](https://www.wikiwand.com/en/Backtracking)]

## Why 

Backtracking can be applied only for problems which admit the concept of a "**partial candidate solution**" and a relatively quick test of whether it can possibly be completed to a valid solution. It is useless, for example, for locating a given value in an unordered table. When it is applicable, however, backtracking is often **much faster than brute force enumeration** of all complete candidates, since it can eliminate many candidates with a single test.

Backtracking is an important tool for solving **constraint satisfaction problems**,[3] such as crosswords, verbal arithmetic, Sudoku, and many other puzzles. It is often the most **convenient** (if not the most efficient[citation needed]) technique for parsing,[4] for 

* **the knapsack problem** and 
* other **combinatorial optimization** problems. It is also 
* the basis of the so-called logic programming languages such as Icon, Planner and Prolog.

Backtracking depends on user-given "**black box procedures**" that define the problem to be solved, the nature of the partial candidates, and how they are extended into complete candidates. It is therefore a metaheuristic rather than a specific algorithm – although, unlike many other meta-heuristics, it is **guaranteed** to find all solutions to a finite problem in a bounded amount of time.

## How

The backtracking algorithm enumerates a set of **partial candidates** that, in principle, could be **completed** in various ways to give all the possible solutions to the given problem. The completion is done **incrementally**, by a sequence of candidate extension steps.

### Pseudocode

In order to apply backtracking to a specific class of problems, one must provide the data P for the particular instance of the problem that is to be solved, and six procedural parameters, **root, reject, accept, first, next, and output**. These procedures should take the instance data P as a parameter and should do the following:

1. `root(P)`: return the partial candidate at the root of the search tree.
1. `reject(P,c)`: return true only if the partial candidate c is not worth completing.
1. `accept(P,c)`: return true if c is a solution of P, and false otherwise.
1. `first(P,c)`: generate the first extension of candidate c.
1. `next(P,s)`: generate the next alternative extension of a candidate, after the extension s.
1. `output(P,c)`: use the solution c of P, as appropriate to the application.

The backtracking algorithm reduces the problem to the call `bt(root(P))`, where bt is the following recursive procedure:

``` python
procedure bt(c) is
    if reject(P, c) then return
    if accept(P, c) then output(P, c)
    s ← first(P, c)
    while s ≠ NULL do
        bt(s)
        s ← next(P, s)
```

* bt: the recursive procedure
* P: the instance data
* c: solution
* s: the extension 

### Others

* Usage considerations
* Early stopping variants

## What 

### Overview

Backtracking is a general algorithm for **finding all (or some) solutions** to some **computational problems**, notably **constraint satisfaction problems**, that **incrementally** **builds** candidates to the solutions, and **abandons** a candidate ("backtracks") as soon as it determines that the candidate cannot possibly be completed to a valid solution.

### Example 

The classic textbook example of the use of backtracking is the eight queens puzzle, that asks for all arrangements of eight chess queens on a standard chessboard so that no queen attacks any other. In the common backtracking approach, the partial candidates are arrangements of k queens in the first k rows of the board, all in different rows and columns. Any partial solution that contains two mutually attacking queens can be abandoned.

Examples where backtracking can be used to solve puzzles or problems include:

* **Puzzles** such as eight queens puzzle, crosswords, verbal arithmetic, Sudoku[nb 1], and Peg Solitaire.
* **Combinatorial optimization** problems such as parsing and the knapsack problem.
* **Logic programming languages** such as Icon, Planner and Prolog, which use backtracking internally to generate answers.

### History

The term "backtrack" was coined by American mathematician D. H. Lehmer in the 1950s.[5] The pioneer string-processing language SNOBOL (1962) may have been the first to provide a built-in general backtracking facility.



### Others

* Description of the method


## FAQs

#### Q: backtracking vs DFS?

A: 2 major differences: 

* DFS handles an **explicit** tree while Backtracking handles an **implicit** tree.
* Depth First Search is a special type of **backtracking algorithmic design paradigm** where the process of backtracking takes place in the **leaf nodes**. In case of backtracking,the algorithm also rejects the useless branch of the state-space tree.This is why DFS maintains the entire tree structure while Backtracking maintaines a pruned tree.

source: [leetcode](https://leetcode.com/discuss/general-discussion/136503/what-is-difference-between-backtracking-and-depth-first-search)

Backtracking is a more general purpose algorithm.

Depth-First search is a specific form of backtracking related to searching tree structures. 

It uses backtracking as part of its means of working with a tree, but is limited to a tree structure.

Backtracking, though, can be used on any type of structure where portions of the domain can be eliminated - whether or not it is a logical tree. The Wiki example uses a chessboard and a specific problem - you can look at a specific move, and eliminate it, then backtrack to the next possible move, eliminate it, etc.

source: [stackoverflow](https://stackoverflow.com/questions/1294720/whats-the-difference-between-backtracking-and-depth-first-search)


