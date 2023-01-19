#### Searching Algorithm
- [Searching Algorithm](#searching-algorithm)
- [Linear Search](#linear-search)
- [Binary Search](#binary-search)
- [Ternary Search](#ternary-search)
- [Jump Search](#jump-search)
- [Exponentional Search](#exponentional-search)

---
#### Linear Search
- **Iterate** over a list, inspect each item, if find it we return index otherwise return -1.

|  | Best | Worst |
| :--- | :---: | :---: |
| Time Complexity | $O(1)$ | $O(n)$ |

```Java
public int linearSearch(int[] array, int target) {
    for (var i = 0; i < array.length; i++)
        if (array[i] == target)
            return i;

    return -1;
}
```  
---
#### Binary Search
- It is **faster than Linear Search**.
- Only **works** on **sorted list**.

|  | Recursive | Iterative |
| :--- | :---: | :---: |
| Time Complexity | $O(\log n)$ | |
| Space Complexity | $O(\log n)$ | $O(1)$ |

```Java
public int binarySearchRec(int[] array, int target) {
    return binarySearchRec(array, target, 0, array.length - 1);
}

private int binarySearchRec(
    int[] array, int target, int left, int right) {

    if (right < left)
        return -1;

    int middle = (left + right) / 2;

    if (array[middle] == target)
        return middle;

    if (target < array[middle])
        return binarySearchRec(array, target, left, middle - 1);

    return binarySearchRec(array, target, middle + 1, right);
}

public int binarySearch(int[] array, int target) {
    var left = 0;
    var right = array.length - 1;

    while (left <= right) {
        var middle = (left + right) / 2;

        if (array[middle] == target)
            return middle;

        if (target < array[middle])
            right = middle - 1;
        else
            left = middle + 1;
    }

    return -1;
}
```
---
#### Ternary Search
- similar to Binary Search
- instead of dividing the list into the half at every step, divide into three parts.
- Binary Search is faster than Ternay Search.

|  | Binary Search | Ternary Search |
| :--- | :---: | :---: |
| Comparisons | 3 | 5 |
| Time Complexity | $O(\log_2 n)$ | $O(\log_3 n)$ |

```Java
public int ternarySearch(int[] array, int target) {
    return ternarySearch(array, target, 0, array.length - 1);
}

private int ternarySearch(
    int[] array, int target, int left, int right) {

    if (left > right)
        return -1;

    int partitionSize = (right - left) / 3;
    int mid1 = left + partitionSize;
    int mid2 = right - partitionSize;

    if (array[mid1] == target)
        return mid1;

    if (array[mid2] == target)
        return mid2;

    if (target < array[mid1])
        return ternarySearch(array, target, left, mid1 - 1);

    if (target > array[mid2])
        return ternarySearch(array, target, mid2 + 1, right);

    return ternarySearch(array, target, mid1 + 1, mid2 - 1);
}
```
---
#### Jump Search
- improvement of Linear Search.
- it's not as fast as Binary Search.
- we divide a list into a few blocks, instead of checking every time, we jump to the block where target item may exist, then we do a Linear Search in that block.

|  | Jump Search |
| :--- | :---: |
| Time Complexity | $O(\sqrt{n})$ |

```Java
public int jumpSearch(int[] array, int target) {
    int blockSize = (int) Math.sqrt(array.length);
    int start = 0;
    int next = blockSize;

    while (start < array.length && array[next - 1] < target) {
        start = next;
        next += blockSize;
        if (next > array.length)
            next = array.length;
    }

    for (var i = start; i < next; i++)
        if (array[i] == target)
            return i;

    return -1;
}
```
---
#### Exponentional Search
- start with a small range of a list, and see if the target item is in that range or not, if not, double the range each step.
- if it find range, then do the Binary Search is that range.

|  | Jump Search | |
| :--- | :---: | :---: | 
| Time Complexity | $O(\log i)$ | i = place of item in the list |

```Java
public int exponentialSearch(int[] array, int target) {

    int bound = 1;
    while (bound < array.length && array[bound] < target)
        bound *= 2;

    int left = bound / 2;
    int right = Math.min(bound, array.length - 1);

    return binarySearchRec(array, target, left, right);
}
```
