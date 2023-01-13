#### Sorting Algorithms
- Comparison Sorts
    - [Bubble Sort](#bubble-sort) 
    - [Selection Sort](#insertion-sort)
    - [Insertion Sort](#insertion-sort)
    - [Merge Sort](#merge-sort)
    - [Quick Sort](#quick-sort)
    - [Bucket Sort](#bucket-sort)
- Non-Comparison Sorts
    - [Counting](#counting-sort)
    - [Bucket](#bubble-sort)
    - Radix 

---
#### Bubble Sort
- We **scan** the array **from left to right**.
- **after each iteration/path** `next largest item` **moves** to its correct position.
- comparisons will be **amount of items count**.
 
|  | Best | Worst |
| :--- | :---: | :---: |
| Passes | $O(1)$ | $O(n)$ |
| Comparisons | $O(n)$ | $O(n)$ |
| **Total** | $O(n)$ | $O(n^2)$ |
| | Linear | Quadratic |

```Java
public class BubbleSort {
    public void sort(int[] array) {
        boolean isSorted;
        for (var i = 0; i < array.length; i++) {
            isSorted = true;
            for (var j = 1; j < array.length - i; j++) {
                if (array[j - 1] > array[j]) {
                    swap(array, j - 1, j);
                    isSorted = false;
                }
            }
      
            if (isSorted)
                return;
        }
    }



    private void swap(int[] array, int index1, int index2) {
        var temp = array[index1];
        array[index1] = array[index2];
        array[index2] = temp;
    }
}
```
---
#### Selection Sort
- **like Bubble Sort** we need multiple pathes to sort an array.
- **in each path** we should find the `next smallest item` and **moves** it to correct position.

|  | Best | Worst |
| :--- | :---: | :---: |
| Passes | $O(n)$ | $O(n)$ |
| Comparisons | $O(n)$ | $O(n)$ |
| **Total** | $O(n^2)$ | $O(n^2)$ |
| | Quadratic | Quadratic |

```Java
public class SelectionSort {
    public void sort(int[] array) {
        for (var i = 0; i < array.length; i++) {
            var minIndex = i;
            for (var j = i; j < array.length; j++)
                if (array[j] < array[minIndex])
                    minIndex = j;
      
            swap(array, minIndex, i);
        }
    }

    private void swap(int[] array, int index1, int index2) {
        var temp = array[index1];
        array[index1] = array[index2];
        array[index2] = temp;
    }
}
```
---
#### Insertion Sort
- every time you **get an item**, you **insert it** in the correct position.
- in the first item, we assume it is in the correct position.
- type of this sort is **based on shifting, not swapping**.

|  | Best | Worst |
| :--- | :---: | :---: |
| Iteration | $O(n)$ | $O(n)$ |
| Shift Items | $O(1)$ | $O(n)$ |
| **Total** | $O(n)$ | $O(n^2)$ |
| | Linear | Quadratic |

```Java
public class InsertionSort {
    public void sort(int[] array) {
        for (var i = 1; i < array.length; i++) {
            var current = array[i];
            var j = i - 1;
            while (j >= 0 && array[j] > current) {
                array[j + 1] = array[j];
                j--;
            }
      
            array[j + 1] = current;
        }
    }
}
```
---
#### Merge Sort
- it's called **Divide and Conquer algorithm**.
- it works by recursively dividing a problem into smaller sub-problems until they become easy to solve then combine the solutions to build the solution to the original problem.

|  | Best | Worst |
| :--- | :---: | :---: |
| Dividing | $O(log n)$ | $O(log n)$ |
| Merging | $O(n)$ | $O(n)$ |
| **Total** | $O(nlog n)$ | $O(nlog n)$ |
| `Space` | $O(n)$ | $O(n)$ |

```Java
public class MergeSort {
    public void sort(int[] array) {
        if (array.length < 2)
            return;

        var middle = array.length / 2;

        int[] left = new int[middle];
        for (var i = 0; i < middle; i++)
            left[i] = array[i];

        int[] right = new int[array.length - middle];
        for (var i = middle; i < array.length; i++)
            right[i - middle] = array[i];

        sort(left);
        sort(right);

        merge(left, right, array);
    }

    private void merge(int[] left, int[] right, int[] result) {
        int i = 0, j = 0, k = 0;

        while (i < left.length && j < right.length) {
            if (left[i] <= right[j])
                result[k++] = left[i++];
            else
                result[k++] = right[j++];
        }

        while (i < left.length)
            result[k++] = left[i++];

        while (j < right.length)
            result[k++] = right[j++];
    }
}
```
---
#### Quick Sort
- it is one of the **most used algorithm**.
- it is a **fairly efficient algorithm** and **unlike Merge Sort** it doesn't require additional space.
- **use partitioning** to make sorting happen.
- Pivot Selection
    - Pick randomly.
    - Use the middle index.
    - Average of first, middle and last item.

|  | Best | Worst |
| :--- | :---: | :---: |
| Partitioning | $O(n)$ | $O(n)$ |
| Of Times | $O(log n)$ | $O(n)$ |
| **Total** | $O(nlog n)$ | $O(n^2)$ |
| `Space` | $O(log n)$ | $O(n)$ |

```Java
public class QuickSort {
    public void sort(int[] array) {
        sort(array, 0, array.length - 1);
    }

    private void sort(int[] array, int start, int end) {
        if (start >= end)
            return;

        var boundary = partition(array, start, end);

        sort(array, start, boundary - 1);
        sort(array, boundary + 1, end);
    }

    private int partition(int[] array, int start, int end) {
        var pivot = array[end];
        var boundary = start - 1;
        for (var i = start; i <= end; i++)
            if (array[i] <= pivot)
                swap(array, i, ++boundary);

        return boundary;
    }

    private void swap(int[] array, int index1, int index2) {
        var temp = array[index1];
        array[index1] = array[index2];
        array[index2] = temp;
    }
}
```
---
#### Counting Sort
- **use two arrays** to make sorting.
- in the end **update Range Array**.
- there is a **trade-off between time and memory**.
- it's just **for integers**.
- When to use
    - allocating extra space is not an issue.
    - values are positive integers.
    - most of the values in the range are present. 

|  | Worst |
| :--- | :---: |
| Populate Counts | $O(n)$ |
| Iterate Counts | $O(k)$ |
| **Total** | $O(n + k)$ = $O(n)$ |
| `Space` | $O(k)$ |

```Java
public class CountingSort {
    public void sort(int[] array, int max) {
        int[] counts = new int[max + 1];
        for (var item : array)
            counts[item]++;

        var k = 0;
        for (var i = 0; i < counts.length; i++)
            for (var j = 0; j < counts[i]; j++)
                array[k++] = i;
    }
}
```
---
#### Bucket Sort
- distribute items in a number of buckets, then buckets by another sorting algorithm and in the end combine them.

| Time | Best | Worst |
| :--- | :---: | :---: |
| distribution | $O(n)$ | $O(n)$ |
| Iterating buckets | $O(k)$ | $O(k)$ |
| Sorting | $O(1)$ | $O(n^2)$ |
| **Total** | $O(n + k)$ | $O(n^2)$ |
| `Space` | $O(n + k)$ |

```Java
public class BucketSort {
    public void sort(int[] array, int numberOfBuckets) {
        var i = 0;
        for (var bucket : createBuckets(array, numberOfBuckets)) {
            Collections.sort(bucket);
            for (var item : bucket)
                array[i++] = item;
        }
    }

    private List<List<Integer>> createBuckets(int[] array, int numberOfBuckets) {
        List<List<Integer>> buckets = new ArrayList<>();
        for (var i = 0; i < numberOfBuckets; i++)
            buckets.add(new ArrayList<>());

        for (var item : array)
            buckets.get(item / numberOfBuckets).add(item);

        return buckets;
    }
}
```
