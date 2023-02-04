#### What are Data Structures?

-   It is **a storage** that is used to **store and organize data**.
-   It is **a way of arranging data** on a computer so that it can be accessed and updated efficiently.
-   Data structure and **data types** are slightly different. Data structure is **the collection of data types** arranged in a specific order.

#### Types of Data Structure

-   Linear data structure
    -   The elements are **arranged in sequence one after the other**.
    -   Since elements are arranged in particular order, they are easy to implement.
-   Non-linear data structure
    -   The elements are not in any sequence.
    -   Instead they are arranged in a hierarchical manner where one element will be connected to one or more elements.

#### Linear data structures

1. [Array Data Structure](./linear-data-structures/array.md)
    - In an array, elements in memory are arranged in continuous memory.
    - All the elements of an array are of the same type.
    - The type of elements that can be stored in the form of arrays is determined by the programming language.
2. [Linked List Data Structure](./linear-data-structures/linked-list.md)
    - Elements are connected through a series of nodes. And, each node contains the data items and address to the next node.
3. [Stack Data Structure](./linear-data-structures/stack.md)
    - Elements are stored in the LIFO principle. That is, the last element stored in a stack will be removed first.
    - It works just like a pile of plates where the last plate kept on the pile will be removed first.
4. [Queue Data Structure](./linear-data-structures/queue-by-array.md)
    - Elements are stored in the FIFO principle where first element stored in the queue will be removed first.
    - It works just like a queue of people in the ticket counter where first person on the queue will get the ticket first.

#### Non linear data structures

1. Graph Data Structure
    - Spanning Tree and Minimum Spanning Tree
    - Strongly Connected Components
    - Adjacency Matrix
    - Adjacency List
2. Trees Data Structure
    - Binary Tree
    - Binary Search Tree
    - AVL Tree
    - B-Tree
    - B+ Tree
    - Red-Black Tree

| Linear Data Structures                                                                                                                            | Non Linear Data Structures                                                                                                                     |
| :------------------------------------------------------------------------------------------------------------------------------------------------ | :--------------------------------------------------------------------------------------------------------------------------------------------- |
| The data items are arranged in sequential order, one after the other.                                                                             | The data items are arranged in non-sequential order (hierarchical manner).                                                                     |
| All the items are present on the single layer.                                                                                                    | The data items are present at different layers.                                                                                                |
| It can be traversed on a single run. That is, if we start from the first element, we can traverse all the elements sequentially in a single pass. | It requires multiple runs. That is, if we start from the first element it might not be possible to traverse all the elements in a single pass. |
| The memory utilization is not efficient.                                                                                                          | Different structures utilize memory in different efficient ways depending on the need.                                                         |
| The time complexity increase with the data size.                                                                                                  | Time complexity remains the same.                                                                                                              |
| Arrays, Stack, Queue                                                                                                                              | Tree, Graph, Map                                                                                                                               |
