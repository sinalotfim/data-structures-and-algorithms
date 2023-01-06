#### Bubble Sort
- We scan the array from left to right.
- after each iteration/path next largest item moves to its corret position.
- comparisons will be amount of items count
 
|  | Best | Worst |
| :--- | :---: | :---: |
| Passes | $O(1)$ | $O(n)$ |
| Comparisons | $O(n)$ | $O(n)$ |
| Total | $O(n)$ | $O(n^2)$ |
| | Linear | Quadratic |

---
#### Selection Sort
- like Bubble Sort we need multiple pathes to sort an array.
- in each path we should find the next smallest item and move it to correct position.

|  | Best | Worst |
| :--- | :---: | :---: |
| Passes | $O(n)$ | $O(n)$ |
| Comparisons | $O(n)$ | $O(n)$ |
| Total | $O(n^2)$ | $O(n^2)$ |
| | Quadratic | Quadratic |

---
#### Insertion Sort
- every time you get an item, you insert it in the correct position.
- in the first item, we assume it is in the correct position.
- type of this sort is based on shifting, not swapping

|  | Best | Worst |
| :--- | :---: | :---: |
| Iteration | $O(n)$ | $O(n)$ |
| Shift Items | $O(1)$ | $O(n)$ |
| Total | $O(n)$ | $O(n^2)$ |
| | Linear | Quadratic |

---
#### Merge Sort
- it's called Divide and Conquer algorithm.
- it works by recursively dividing a problem into smaller sub-problems until they become easy to solve then combine the solutions to build the solution to the originak problem.
- type of this sort is based on shifting, not swapping

|  | Best | Worst |
| :--- | :---: | :---: |
| Dividing | $O(log n)$ | $O(log n)$ |
| Merging | $O(1)$ | $O(n)$ |
| Total | $O(nlog n)$ | $O(nlog n)$ |
| Space | $O(n)$ | $O(n)$ |

#### Quick Sort
- it is one of the most used algorithm.
- it is a fairly efficient algorithm and unlike Merge Sort it doesn't require additional space.
- use partitioning to make sorting happen.
- Pivot Selection
    - Pick randomly.
    - Use the middle index.
    - Average of first, middle and last item.

|  | Best | Worst |
| :--- | :---: | :---: |
| Partitioning | $O(n)$ | $O(n)$ |
| Of Times | $O(log n)$ | $O(n)$ |
| Total | $O(nlog n)$ | $O(n^2)$ |
| Space | $O(log n)$ | $O(n)$ |

#### Counting Sort
- use two arrays to make sorting.
- in the end update Range Array
- there is a trade-off between time and memory.
- When to use
    - allocating extra space is not an issue.
    - values are positive integers.
    - most of the values in the range are present. 

|  | Worst |
| :--- | :---: |
| Populate Counts | $O(n)$ |
| Iterate Counts | $O(k)$ |
| Total | $O(n + k)$ |
| Space | $O(k)$ |
