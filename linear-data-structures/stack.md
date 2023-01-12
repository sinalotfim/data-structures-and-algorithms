#### Stack
- Last-In First-Out (**LIFO**).
- Stack Can be implemented by using **Arrays** and **Linked lists**.
- Stack operations
    - `push`: add an item on top of the stack.
    - `pop`: remove and return an item on top of the stack.
    - `peek`: return an item on the top of the stack without removing it.
- Usings
    - Implement the **undo feature**.
    - Build **compilers** (e.g. syntax checking)
    - **Evaluate expressions** (e.g. 1+2*3)
    - **Build navigation** (e.g. forward/back)

| Operation | Approximation |
| :--- | :---: |
| Lookup | $O(1)$ |
| Insert | $O(1)$ |
| Delete | $O(1)$ |

---
#### Q: Create a stack is composed of the following methods:
- [x] [push](#a-push)
- [x] [pop](#a-pop)
- [x] [peek](#a-peek)
- [x] [isEmpty](#a-isempty)
- [x] [size](#a-size)

---
#### A: Structure of a stack
```Java
public class Stack {
    private int[] items;
    private int count;

    public Stack(int capacity) {
        items = new int[capacity];
    }

    @Override
    public String toString() {
        var newItems = Arrays.copyOfRange(items, 0, count);
        return Arrays.toString(newItems);
    }
}
```
---
#### A: push
```Java
private boolean isFull() {
    return items.length == count;
}

public void push(int item) {
    if (isFull())
        throw new StackOverflowError();

    items[count++] = item;
}
```
---
#### A: pop
```Java
public int pop() {
    if (isEmpty())
        throw new IllegalStateException();

    return items[--count];
}
```
---
#### A: peek
```Java
public int peek() {
    if (isEmpty())
        throw new IllegalStateException();

    return items[count - 1];
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