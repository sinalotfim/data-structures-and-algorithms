#### Q: Create a queue is comprising the following methods:
- [x] [enqueue](#a-enqueue)
- [x] [dequeue](#a-dequeue)
- [x] [peek](#a-peek)

---
##### A: Structure of a stack
```Java
public class ArrayQueue {
    private int[] items;
    private int rear;
    private int front;
    private int count;

    public ArrayQueue(int capacity) {
        items = new int[capacity];
    }

    @Override
    public String toString() {
        return Arrays.toString(items);
    }
}
```
---
##### A: enqueue
```Java
public void enqueue(int item) {
    if (isFull()) throw new IllegalStateException();

    items[rear] = item;
    rear = (rear + 1) % items.length;
    count++;
}

public boolean isFull() {
    return count == items.length;
}
```
---
##### A: dequeue
```Java
public int dequeue() {
    if (isEmpty()) throw new IllegalStateException();

    var item = items[front];
    items[front] = 0;
    front = (front + 1) % items.length;
    count--;

    return item;
}

public boolean isEmpty() {
    return count == 0;
}
```
---
##### A: peek
```Java 
public int peek() {
    if (isEmpty()) throw new IllegalStateException();
    return items[front];
}
```