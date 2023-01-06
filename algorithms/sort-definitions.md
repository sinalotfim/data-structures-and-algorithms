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
