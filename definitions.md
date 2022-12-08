Big-O notation
    - Big-O notation is a mathematical notation that describes the limiting bahavior of a function when the argument tends towards a particular value or infinity.
    - We use Big-O to describe the performance of an algorithem.
    - We need opproximation cost of an algorithem in Big-O, so we can drop constant value

Linear Search -> O(n)
Binary Search -> Log n

O(n)        -> Constant 
O(Log n)    -> Logarithmic
O(n)        -> Linear
O(n^2)      -> Quadratic
O(2^n)      -> Exponential

Array
    - A list of items store sequentially.
    - Lookup 
      - By index    -> O(1)
      - By value    -> O(n)
    - Insert        -> O(n)
    - Delete        -> O(n)

Linked list
    - A list of items that store sequentially and can grow and shrink automatically
    - Lookup 
      - By index            -> O(1)
      - By value            -> O(n)
    - Insert
      - At the beginning    -> O(1)
      - At the end          -> O(1)
      - In the middle       -> O(n)
    - Delete
      - From the beginning  -> O(1)
      - From the end        -> O(n)
      - From the middle     -> O(n)