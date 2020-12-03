<h1 align="center">
<br>
	<a href="https://ece.uwaterloo.ca/~dwharder/aads/Abstract_data_types/">
  <img src="https://i.imgur.com/r8DOA1Q.png" alt="Abstract Data Types: Map" width=42%">
  </a>
  <br><br>
Container (abstract data type)
  <br><br>
</h1>

> they store objects in an organized way that follows specific access rules. [[wiki](https://www.wikiwand.com/en/Container_(abstract_data_type))]

## Why 

provide **flexibility** in choosing the right implementation for any given scenario

## How



## What 

### overview

In computer science, a container is a **class**, a **data structure**, or **an abstract data type** (ADT) whose instances are collections of other objects. In other words, they **store** objects in an **organized** way that follows specific access **rules**. The **size** of the container depends on the number of objects (elements) it contains. Underlying (inherited) **implementations** of various container types may vary in size and complexity, and provide **flexibility** in choosing the right implementation for any given scenario.

### anatomy (properties)

Containers can be characterized by the following three properties:

* **access**, that is the way of accessing the objects of the container. In the case of arrays, access is done with the array index. In the case of stacks, access is done according to the LIFO (last in, first out) order and in the case of queues it is done according to the FIFO (first in, first out) order;
* **storage**, that is the way of storing the objects of the container;
* **traversal**, that is the way of traversing the objects of the container.

Container classes are expected to implement **methods** to do the following:

* **create** an empty container (constructor);
* **insert** objects into the container;
* **delete** objects from the container;
* **delete** **all** the objects in the container (**clear**);
* **access** the **objects** in the container;
* **access** the **number** of objects in the container (**count**).

### types

Containers may be classified as either **single-value** containers or **associative** containers.

Container abstract data types include:

* FIFO queues
* LIFO stacks
* Priority queues
* Lookup tables (LUTs)
* Key-associated data structures
	* Sets, containing and indexing objects by value or by specific property;
	* Maps, associating to each key a "value" for lookup



## FAQs

#### Q: Comparison of static vs dynamic data structures?

A: source: [computersciencewiki.org](https://computersciencewiki.org/index.php/Abstract_data_structures#Comparison_of_different_data_structures)

#### Q: Which data structure to use?

A: [Choosing which data structure to use](https://computersciencewiki.org/index.php/Abstract_data_structures#Choosing_which_data_structure_to_use)

