#### List of solutions can be resolved by Stack
- [x] [Implement a min heap.](#q-implement-a-min-heap)
- [x] [Implement a min priority queue.](#q-implement-a-min-priority-queue)
- [x] [Building a PriorityQueue with the Heap.](#q-implement-a-min-priority-queue)
- [x] [Heapify algorithm](#)

---
##### Q: Implement a min heap.
```Java
public class MinHeap {
    private class Node {
        private int key;
        private String value;

        public Node(int key, String value) {
            this.key = key;
            this.value = value;
        }
    }

    private Node[] nodes = new Node[10];
    private int size;

    public void insert(int key, String value) {
        if (isFull())
            throw new IllegalStateException();

        nodes[size++] = new Node(key, value);

        bubbleUp();
    }

    public String remove() {
        if (isEmpty())
            throw new IllegalStateException();

        var root = nodes[0].value;
        nodes[0] = nodes[--size];

        bubbleDown();

        return root;
    }

    private void bubbleDown() {
        var index = 0;
        while (index <= size && !isValidParent(index)) {
            var largerChildIndex = smallerChildIndex(index);
            swap(index, largerChildIndex);
            index = largerChildIndex;
        }
    }

    public boolean isEmpty() {
        return size == 0;
    }

    private int smallerChildIndex(int index) {
        if (!hasLeftChild(index))
            return index;

        if (!hasRightChild(index))
            return leftChildIndex(index);

        return (leftChild(index).key < rightChild(index).key) ?
                leftChildIndex(index) :
                rightChildIndex(index);
    }

    private boolean hasLeftChild(int index) {
        return leftChildIndex(index) <= size;
    }

    private boolean hasRightChild(int index) {
        return rightChildIndex(index) <= size;
    }

    private boolean isValidParent(int index) {
        if (!hasLeftChild(index))
            return true;

        var isValid = nodes[index].key <= leftChild(index).key;

        if (hasRightChild(index))
            isValid &= nodes[index].key <= rightChild(index).key;

        return isValid;
    }

    private Node rightChild(int index) {
        return nodes[rightChildIndex(index)];
    }

    private Node leftChild(int index) {
        return nodes[leftChildIndex(index)];
    }

    private int leftChildIndex(int index) {
        return index * 2 + 1;
    }

    private int rightChildIndex(int index) {
        return index * 2 + 2;
    }

    public boolean isFull() {
        return size == nodes.length;
    }

    private void bubbleUp() {
        var index = size - 1;
        while (index > 0 && nodes[index].key < nodes[parent(index)].key) {
            swap(index, parent(index));
            index = parent(index);
        }
    }

    private int parent(int index) {
        return (index - 1) / 2;
    }

    private void swap(int first, int second) {
        var temp = nodes[first];
        nodes[first] = nodes[second];
        nodes[second] = temp;
    }
}
```
---
##### Q: Implement a min priority queue.
```Java
public class MinPriorityQueue {
    private MinHeap heap = new MinHeap();

    public void add(String value, int priority) {
        heap.insert(priority, value);
    }

    public String remove() {
        return heap.remove();
    }

    public boolean isEmpty() {
        return heap.isEmpty();
    }
}
```
---
##### Q: Building a PriorityQueue with the Heap.
```Java
public class PriorityQueueWithHeap {
  private Heap heap = new Heap();

  // O(log n)
  public void enqueue(int item) {
    heap.insert(item);
  }

  // O(log n)
  public int dequeue() {
    return heap.remove();
  }

  public boolean isEmpty() {
    return heap.isEmpty();
  }
}
```
---
##### Q: Heapify algorithm
```Java
public class MaxHeap {
  public static void heapify(int[] array) {
    var lastParentIndex = array.length / 2 - 1;
    for (var i = lastParentIndex; i >= 0; i--)
      heapify(array, i);
  }

  private static void heapify(int[] array, int index) {
    var largerIndex = index;

    var leftIndex = index * 2 + 1;
    if (leftIndex < array.length &&
        array[leftIndex] > array[largerIndex])
      largerIndex = leftIndex;

    var rightIndex = index * 2 + 2;
    if (rightIndex < array.length &&
      array[rightIndex] > array[largerIndex])
      largerIndex = rightIndex;

    if (index == largerIndex)
      return;

    swap(array, index, largerIndex);
    heapify(array, largerIndex);
  }

  private static void swap(int[] array, int first, int second) {
    var temp = array[first];
    array[first] = array[second];
    array[second] = temp;
  }

  public static int getKthLargest(int[] array, int k) {
    if (k < 1 || k > array.length)
      throw new IllegalArgumentException();

    var heap = new Heap();
    for (var number : array)
      heap.insert(number);

    for (var i = 0; i < k - 1; i++)
      heap.remove();

    return heap.max();
  }
}
```
