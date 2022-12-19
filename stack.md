#### Q: Create a stack is comprising the following methods:
- [x] [push](#a-push)
- [x] [pop](#a-pop)
- [x] [peek](#a-peek)

---
#### A: Structure of a stack
```Java
public class Stack {
    private int[] items = new int[5];
    private int count;

    @Override
    public String toString() {
        var content = Arrays.copyOfRange(items, 0, count);
        return Arrays.toString(content);
    }
}
```
---
#### A: push
```Java
public boolean isFull() {
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
public boolean isEmpty() {
    return count == 0;
}

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