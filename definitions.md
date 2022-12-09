##### Big-O Notation
- Big-O Notation is a **mathematical notation** that describes the **limiting bahavior** of a function when the argument tends towards a particular value or infinity.
- We use Big-O Notation to describe the **performance of an algorithm**.
- We need opproximation cost of an algorithem in Big-O, so we can **drop constant value**.

##### Some popular complexity of an algorithm
| Name | Approximation |
| :--- | :---: |
| Constant | $(n)$ |
| Logarithmic | $(log n)$ |
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
| Lookup - **by index** | $O(1)$ |
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

| Operation | Approximation |
| :--- | :---: |
| Lookup | $O(1)$ |
| Insert | $O(1)$ |
| Delete | $O(1)$ |