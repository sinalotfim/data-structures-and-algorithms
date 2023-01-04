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