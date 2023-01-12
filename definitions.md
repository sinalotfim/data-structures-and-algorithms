#### Big-O Notation
- Big-O Notation is a **mathematical notation** that describes the **limiting bahavior** of a function when the **argument tends towards a particular value or infinity**.
- We use Big-O Notation to describe the **performance of an algorithm**.
- We need **opproximation cost of an algorithem** in Big-O, so we can **drop constant value**.
- Some popular complexities of an algorithm 
 
| Name | Approximation |
| :--- | :---: |
| Constant | $(n)$ |
| Logarithmic | $O(log n)$ |
| Linear | $O(n)$ |
| Quadratic | $O(n^2)$ |
| Exponential | $O(2^n)$ |

---
#### Tree
- It is a Data Structure that **stores elements in a hierachy**.
- It refers its elements as **Node** and **Line** that connects them as **Edges**.
- Types
    - Binary Tree
        - Binary Search Tree
            - AVL Tree 
        - Prefect Tree
        - Complete Tree
            - Heap 
    - Perfect Tree
    - Complete Tree
    - Balanced Tree
    - Right Skewed Binary Tree
    - Left Skewed Binary Tree
- Usages
    - Represents hierachical data
    - Databases
    - Autocompletion
    - Compilers
    - Compression (JPEG, MP3)
---
##### Perfect Tree
- Every level except the **last level** is full of nodes.
##### Complete Tree
- Eevery level except the **last level** is **completely filled** and the levels **are filled from the left to the right**.
- Types
    - Heap 
##### Balanced Tree
- ```Java 
    height(left) - height(right) <= 1
  ```
##### Right Skewed Binary Tree / Left Skewed Binary Tree
- The most worst tree is right skewed or left skewed tree, it's not tree, it's like linked list.
---
#### Self-Balancing Trees
- AVL Trees (Aelson-Velsky and Landis)
- Red-Black Trees
- B-Trees
- Splay Trees
- 2-3 Trees




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