#### Array

-   A **list of items** store **sequentially**.

| Operation             | Approximation |
| :-------------------- | :-----------: |
| Lookup - **by index** |    $O(1)$     |
| Lookup - **by value** |    $O(n)$     |
| Insert                |    $O(n)$     |
| Delete                |    $O(n)$     |

---

#### Q: Create an `Array` is composed of the following methods:

-   [x] [insert](#a-insert)
-   [x] [insertAt](#a-insertat)
-   [x] [removeAt](#a-removeat)
-   [x] [indexOf](#a-indexof)
-   [x] [contains](#a-contains)
-   [x] [reverse](#a-reverse)
-   [x] [max](#a-max)
-   [x] [intersect](#a-intersect)

#### A: Structure of an array

```Java
public class Array {
    private int[] items;
    private int count;

    public Array(int length) {
        if (length < 0)
            throw new IllegalArgumentException();

        items = new int[length];
    }

    public void print() {
        for(int i = 0; i < count; i++)
            System.out.println(items[i]);
    }

    @Override
    public String toString() {
        int[] newItems = Arrays.copyOfRange(items, 0, count);
        return Arrays.toString(newItems);
    }
}
```

---

#### A: insert

```Java
private boolean isFull() {
    return items.length == count;
}

private void resizeIfRequired() {
    if (isFull()) {
        int[] newItems = new int[count * 2];
        for (int i = 0; i < count; i++)
            newItems[i] = items[i];

        items = newItems;
    }
}

public void insert(int item) {
    resizeIfRequired();
    items[count++] = item;
}
```

---

#### A: insertAt

```Java
public void insertAt(int item, int index) {
    if (index < 0 || index > count)
        throw new IllegalArgumentException();

    resizeIfRequired();

    for (int i = count; i > index; i--)
        items[i] = items[i - 1];

    items[index] = item;
    count++;
}
```

---

#### A: removeAt

```Java
public void removeAt(int index) {
    if (index < 0 || index >= count)
        throw new IllegalArgumentException();

    for (int i = index; i < count - 1; i++)
        items[i] = items[i + 1];

    count--;
}
```

---

#### A: indexOf

```Java
public int indexOf(int item) {
    for (int i = 0; i < count; i++) {
        if (items[i] == item)
            return i;
    }

    return -1;
}
```

---

#### A: contains

```Java
public boolean contains(int item) {
    return indexOf(item) != -1;
}
```

---

#### A: reverse

```Java
public void reverse() {
    int[] newItems = new int[count];
    for (int i = 0; i < count; i++)
        newItems[i] = items[count - 1 - i];

    items = newItems;
}
```

---

#### A: max

```Java
public int max() {
    int max = 0;
    for (int item : items) {
        if (item > max)
            max = item;
    }

    return max;
}
```

---

#### A: intersect

```Java
public Array intersect(Array other) {
    var intersection = new Array(count);

    for (int item : items) {
        if (other.contains(item))
            intersection.insert(item);
    }

    return intersection;
}
```
