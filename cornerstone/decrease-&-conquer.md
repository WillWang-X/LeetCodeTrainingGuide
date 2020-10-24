<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Greedy_algorithm">
  <img src="https://i.imgur.com/Gu5jVjZ.png" alt="decrease and conquer" width=42%">
  </a>
  <br><br>
Decrease and conquer 
  <br><br>
</h1>

> The basic idea of the method is a recursive procedure in which at each step the input size is reduced ("pruned") by a constant factor 0 < p < 1. As such, it is a form of decrease and conquer algorithm, where at each step the decrease is by a constant factor.  [[wiki](https://www.wikiwand.com/en/Prune_and_search)]

## 📝1. Basics

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


## ⚔️2. Use cases

* decrease by one: [78. subset], **240**, **169**
* decrease by a constant factor: binary-search
* variable size decrease: 4, 50


## 🤺3. Best Practices

## 😈4. More training

* 4 Median of Two Sorted Arrays  
* 46 Permutations
* 50 Pow(x, n) 
* 74 Search a 2D Matrix
* 78 Subsets
* 169 Majority Element 
* 240 Search a 2D Matrix II
* 542 01 Matrix 
* 667 Beautiful Arrangement II

## 💬5. Explanation

## ⚠️6. FAQs
