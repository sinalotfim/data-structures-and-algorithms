#### Q: Create a stack is comprising the following methods:
- [x] [push](#a-push)
- [x] [pop](#a-pop)
- [x] [peek](#a-peek)
- [x] [isEmpty](#a-isempty)


---
##### A: Structure of a stack
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
##### A: push
```Java
public void push(int item) {
    if (count == items.length)
        throw new StackOverflowError();

    items[count++] = item;
}
```
---
##### A: pop
```Java
public int pop() {
    if (count == 0)
        throw new IllegalStateException();

    return items[--count];
}
```
---
##### A: peek
```Java
public int peek() {
    if (count == 0)
        throw new IllegalStateException();

    return items[count - 1];
}
```

---
##### A: isEmpty
```Java
public boolean isEmpty() {
    return count == 0;
}
```