# Decrease and conquer 

<center>
<img src="https://i.imgur.com/Gu5jVjZ.png" alt="decrease and conquer" width="200"/> 
<br> 
from *The design and analysis of algorithms*

</center>

## 基础知识

**Decrease-and-conquer** is a general algorithm design technique, based on exploiting **a relationship between a solution to a given instance of a problem and a solution to a smaller instance of the same problem**. Once such a relationship is established, it can be exploited either top down (usually recursively) or bottom up.

There are three major variations of decrease-and-conquer:

* decrease-by-a-constant, most often by one (e.g., **insertion sort**)
* decrease-by-a-constant-factor, most often by the factor of two (e.g., **binary search**)
* variable-size-decrease (e.g., **Euclid’s algorithm**)

Problems:


* Decrease by one 
	* **insertion sort**
	* topological sorting 
	* Generating Combinatorial Objects
		* Generating Permutations
		* Generating Subsets
* Decrease by a constent-factor 
	* Binary Search 
	* Fake-Coin Problem
	* Russian Peasant Multiplication
	* Josephus Problem
* variable-size-decrease
	* Euclid’s algorithm
	* Computing a Median and the **Selection Problem**
	* Interpolation Search
	* Searching and Insertion in a Binary Search Tree
	* The Game of Nim



##  典型应用

* decrease by one: [78. subset], **240**, **169**
* decrease by a constant factor: binary-search
* variable size decrease: 4, 50


## 最佳实践

## 木桩训练

* 4 Median of Two Sorted Arrays  
* 46 Permutations
* 50 Pow(x, n) 
* 74 Search a 2D Matrix
* 78 Subsets
* 169 Majority Element 
* 240 Search a 2D Matrix II
* 542 01 Matrix 
* 667 Beautiful Arrangement II



## Q&A: Question


## Thanks

* 《The design and analysis of algorithms》
