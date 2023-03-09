#### Stack

-   A stack is a linear data structure that follows the principle of **Last In First Out (LIFO)**. This means the last element inserted inside the stack is removed first.
-   The most common **stack implementation** is using <mark>Arrays</mark>, but it can also be implemented using <mark>Linked Lists</mark>.
-   Usages
    -   **To reverse a word** - Put all the letters in a stack and pop them out. Because of the LIFO order of stack, you will get the letters in reverse order.
    -   **In compilers** - Compilers use the stack to calculate the value of expressions like 2 + 4 / 5 \* (7 - 9) by converting the expression to prefix or postfix form.
    -   **In browsers** - The back button in a browser saves all the URLs you have visited previously in a stack. Each time you visit a new page, it is added on top of the stack. When you press the back button, the current URL is removed from the stack, and the previous URL is accessed.
-   You can **think of** the stack data structure as **the pile of plates on top of another**.
    ![Big-O Notation](./assets/../../assets/stack.webp)

#### LIFO Principle of Stack

-   In programming terms, putting an item on top of the stack is called push and removing an item is called pop.
    ![Big-O Notation](./assets/../../assets/stack-lifo.webp)

#### Basic Operations of Stack

1. `push`: Add an element to the top of a stack.
2. `pop`: Remove an element from the top of a stack.
3. `peek`: Get the value of the top element without removing it.
4. `isEmpty`: Check if the stack is empty.
5. `isFull`: Check if the stack is full.

| Operation | Approximation |
| :-------- | :-----------: |
| Lookup    |    $O(1)$     |
| Insert    |    $O(1)$     |
| Delete    |    $O(1)$     |

---

#### Q: Create a `Stack` is composed of the following methods:

-   [x] [structue](#a-structure-of-a-stack)
-   [x] [push](#a-push)
-   [x] [pop](#a-pop)
-   [x] [peek](#a-peek)
-   [x] [isEmpty](#a-isempty)
-   [x] [isFull](#a-isfull)
-   [x] [size](#a-size)

---

#### A: Structure of a stack

```Java
public class Stack {
    private int[] items;
    private int count;

    public Stack(int capacity) {
        if (capacity < 0)
            throw new IllegalArgumentException();

        items = new int[capacity];
    }

    public void print() {
        for(int i = 0; i < count; i++)
            System.out.println(items[i]);
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

#### A: isFull

```Java
public boolean isFull() {
    return count == items.length;
}
```

---

#### A: size

```Java
public int size() {
    return count;
}
```
