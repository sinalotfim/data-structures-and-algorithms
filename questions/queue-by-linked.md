#### Q: Create a queue is composed of the following methods:
- [x] [enqueue](#a-enqueue)
- [x] [dequeue](#a-dequeue)
- [x] [peek](#a-peek)
- [x] [isEmpty](#a-isempty)
- [x] [size](#a-size)

---
#### A: Structure of a stack
```Java
public class LinkedListQueue {
    private class Node {
        private int value;
        private Node next;

        public Node(int value) {
            this.value = value;
        }
    }

    @Override
    public String toString() {
        var list = new ArrayList<>();

        var current = head;
        while (current != null) {
            list.add(current.value);
            current = current.next;
        }

        return list.toString();
    }

    private Node head;
    private Node tail;
    private int count;
}
```
---
#### A: enqueue
```Java
public void enqueue(int item) {
    var node = new Node(item);

    if (isEmpty()) {
        head = tail = node;
    } else {
        tail.next = node;
        tail = node;
    }

    count++;
}
```
---
#### A: dequeue
```Java
public int dequeue() {
    if (isEmpty())
        throw new IllegalStateException();

    int value = head.value;
    if (head == tail) {
        head = tail = null;
    } else {
        var second = head.next;
        head.next = null;
        head = second;
    }

    count--;

    return value;
}
```
---
#### A: peek
```Java 
public int peek() {
    if (isEmpty())
        throw new IllegalStateException();

    return head.value;
}
```
---
#### A: isEmpty
```Java 
public boolean isEmpty() {
    return count == 0;
}
```
---
#### A: size
```Java
public int size() {
    return count;
}
```
