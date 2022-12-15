##### Big-O Notation
- Big-O Notation is a **mathematical notation** that describes the **limiting bahavior** of a function when the argument tends towards a particular value or infinity.
- We use Big-O Notation to describe the **performance of an algorithm**.
- We need opproximation cost of an algorithem in Big-O, so we can **drop constant value**.

##### Some popular complexity of an algorithm
| Name | Approximation |
| :--- | :---: |
| Constant | $(n)$ |
| Logarithmic | $O(log n)$ |
| Linear | $O(n)$ |
| Quadratic | $O(n^2)$ |
| Exponential | $O(2^n)$ |

---
##### Array
- A list of items store sequentially.

| Operation | Approximation |
| :--- | :---: |
| Lookup - **by index** | $O(1)$ |
| Lookup - **by value** | $O(n)$ |
| Insert | $O(n)$ |
| Delete | $O(n)$ |

---
##### Linked List
- A **list of items** that store sequentially and **can grow and shrink automatically**.

| Operation | Approximation |
| :--- | :---: |
| Lookup - **by index** | $O(n)$ |
| Lookup - **by value** | $O(n)$ |
| Insert - **at the beginning** | $O(1)$ |
| Insert - **at the end** | $O(1)$ |
| Insert - **in the middle** | $O(n)$ |
| Delete - **from the beginning**| $O(1)$ |
| Delete - **from the end** | $O(n)$ |
| Delete - **from the middle** | $O(n)$ |

---
##### Stack
- Last-In First-Out (LIFO).
- Can be implemented by using Arrays and Linked lists.
- Stack can be created by Array or Linked List.
- Stack operations
    - `push`: add an item on top of the stack.
    - `pop`: remove and return an item on top of the stack.
    - `peek`: return an item on the top of the stack without removing it.
- Usings
    - Implement the undo feature.
    - Build compilers (e.g. syntax checking)
    - Evaluate expressions (e.g. 1+2*3)
    - Build navigation (e.g. forward/back)

| Operation | Approximation |
| :--- | :---: |
| Lookup | $O(1)$ |
| Insert | $O(1)$ |
| Delete | $O(1)$ |

---
##### Queue
- is a line of items. 
- First-In First-Out (FIFO).
- Sharing a resource amongst many consumers.
- Queue operations
    - `enqueue`: add an item to the back of the queue.
    - `dequeue`: remove an item from the front of the queue
    - `peek`: get the item at the front of the queue without removing item.

| Operation | Approximation |
| :--- | :---: |
| Lookup | $O(1)$ |
| Insert | $O(1)$ |
| Delete | $O(1)$ |
---
#### Hash Tables
- Usings
    - Spell checkers
    - Dictionaries
    - Compilers
    - Code Editors
- Languages
    - Java &rarr; HashMap
    - C# &rarr; Dictionary
    - Python &rarr; Dictionary
    - JavaScript &rarr; Object

| Operation | Approximation |
| :--- | :---: |
| Lookup | $O(1)$ |
| Insert | $O(1)$ |
| Delete | $O(1)$ |