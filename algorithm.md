#### What is an Algorithm?

-   It is **a set of well-defined instructions** to solve a particular problem.
-   It **takes a set of input(s)** and **produces the desired output**.

#### Qualities of a Good Algorithm

-   **Input and output** should be **defined precisely**.
-   **Each step** in the algorithm should be **clear and unambiguous**.
-   Algorithms should be **most effective** among many different ways to solve a problem.
-   An algorithm **shouldn't include computer code**. Instead, the algorithm should be written in such a way that it can be used in different programming languages.



#### Master Theorem

-   The master method is a formula for solving recurrence relations of the form.
-   The master theorem is used in calculating the time complexity of recurrence relations (divide and conquer algorithms) in a simple and quick way.

#### Divide and Conquer Algorithm

-   A divide and conquer algorithm is a strategy of solving a large problem by
    -   breaking the problem into smaller sub-problems
    -   solving the sub-problems, and
    -   combining them to get the desired output.
-   To use the divide and conquer algorithm, recursion is used.
-   The complexity of the **divide and conquer algorithm** is calculated using the **master theorem**.

#### How Divide and Conquer Algorithms Work?

1. **Divide**: Divide the given problem into sub-problems using recursion.
2. **Conquer**: Solve the smaller sub-problems recursively. If the subproblem is small enough, then solve it directly.
3. **Combine**: Combine the solutions of the sub-problems that are part of the recursive process to solve the actual problem.

#### Divide and Conquer Vs Dynamic approach

-   The divide and conquer approach divides a problem into smaller subproblems; these subproblems are further solved recursively. The result of each subproblem is not stored for future reference, whereas, in a dynamic approach, the result of each subproblem is stored for future reference.
-   Use the divide and conquer approach when the same subproblem is not solved multiple times. Use the dynamic approach when the result of a subproblem is to be used multiple times in the future.

#### Advantages of Divide and Conquer Algorithm

-   The complexity for the multiplication of two matrices using the naive method is $O(n^3)$, whereas using the divide and conquer approach (i.e. Strassen's matrix multiplication) is $O(n^{2.8074})$. This approach also simplifies other problems, such as the Tower of Hanoi.
-   This approach is suitable for multiprocessing systems.
-   It makes efficient use of memory caches.

#### Divide and Conquer Applications

1. Binary Search
2. Merge Sort
3. Quick Sort
4. Strassen's Matrix multiplication
5. Karatsuba Algorithm
