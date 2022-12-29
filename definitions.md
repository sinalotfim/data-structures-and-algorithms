##### Big-O Notation
- Big-O Notation is a **mathematical notation** that describes the **limiting bahavior** of a function when the **argument tends towards a particular value or infinity**.
- We use Big-O Notation to describe the **performance of an algorithm**.
- We need **opproximation cost of an algorithem** in Big-O, so we can **drop constant value**.

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
- A **list of items** store **sequentially**.

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
- Last-In First-Out (**LIFO**).
- Stack Can be implemented by using **Arrays** and **Linked lists**.
- Stack operations
    - `push`: add an item on top of the stack.
    - `pop`: remove and return an item on top of the stack.
    - `peek`: return an item on the top of the stack without removing it.
- Usings
    - Implement the **undo feature**.
    - Build **compilers** (e.g. syntax checking)
    - **Evaluate expressions** (e.g. 1+2*3)
    - **Build navigation** (e.g. forward/back)

| Operation | Approximation |
| :--- | :---: |
| Lookup | $O(1)$ |
| Insert | $O(1)$ |
| Delete | $O(1)$ |

---
##### Queue
- A line of items. 
- First-In First-Out (**FIFO**).
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
- store **key/value pairs**
- Collision solving
    - Chaining
    - Open adressing
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
---
#### Tree
- is a Data Structure that **stores elements in a hierachy**.
- refers its elements as **Node** and **Line** that connects them as **Edges**.
- Usings
    - Represents hierachical data
    - Databases
    - Autocompletion
    - Compilers
    - Compression (JPEG, MP3)

##### Binary Tree
- is a **Tree** that every node has **maximum two children**.
- **Left** Node **<** **Root** Node **<** **Right** Node.
- Traversing Trees
    - **Breadth first** (Level order)
    - **Depth first**
        - | Name | Direction | From To / Type | 
          | :--- | :---: | :---: |
          | Pre-order | **Root**, Left, Right | Root to Leafs |
          | In-order (LRR) | Left, **Root**, Right | ASC |
          | In-order (RRL) | Right, **Root**, Left | DESC |
          | Post-order | Left, Right, **Root** | Leafs to Root |
- Tree Depth: From **Bottom to Top** (**BT**)
- Tree Height: From **Top to Bottom** (**TB**) -> **1 + max(height(Left), height(Right))**

| Operation | Approximation |
| :--- | :---: |
| Lookup | $O(log n)$ |
| Insert | $O(log n)$ |
| Delete | $O(log n)$ |

##### Perfect Tree
- every level except the **last level** is full of nodes.
##### Complete Tree
- every level except the **last level** is **completely filled** and the levels **are filled from the left to the right**. 
##### Balanced Tree
- height(left) - height(right) <= 1
##### Right Skewed Binary Tree / Left Skewed Binary Tree
- the most worst tree is right skewed or left skewed tree, it's not tree, it's like linked list.

##### Self-Balancing Trees
- AVL Trees (Aelson-Velsky and Landis)
- Red-Black Trees
- B-Trees
- Splay Trees
- 2-3 Trees

##### AVL Tree
- is a special kind of **Binary Search Tree** that automatically **rebalance themself** every time we add or remove node.
- Rotations
    - Left (LL)
    - Right (RR)
    - Left-Right (LR)
    - Right-Left (RL)


#### Heap
- it is a Complete Tree
- it has a Heap Property
- Heap Property
    - The root node has the largest or smallest value.
    - Max Heap Property
        - the value of every node is greater than or equal to its children.
    - Min Heap Property
        - the value of every node is smaller than or equal to its children.
- Heaps
    - Sorting (HeapSort)
    - Graph algorithms (shortest path)
    - Priority Queues
    - Finding the kth smallest/largest value

| Operation | Approximation |
| :--- | :---: |
| Lookup | $O(log n)$ |
| Insert | $O(log n)$ |
| Delete | $O(log n)$ |

#### Tries
- is another kind of Trees, but they are not Binary Trees that each child can have serveral nodes, and the name actually comes from re**Trie**val.
- Another names for Tries are:
    - Digital
    - Radix
    - Prefix Tree
- important place that you can use Tries is **Autocompletion**.
- Why not Arrays instead of Tries?
    - waste a lot of space because a lot of words have the same prefix
    - looking up word in array is relatively slow.

| Operation | Approximation | |
| :--- | :---: | :---: |
| Lookup | $O(L)$ | L = length of word |
| Insert | $O(L)$ | L = length of word |
| Delete | $O(L)$ | L = length of word |