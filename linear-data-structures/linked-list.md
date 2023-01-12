#### Linked List
- A **list of items** that store sequentially and **can grow and shrink automatically**.

| Operation | Approximation |
| :--- | :---: |
| Lookup - **by index** | $O(n)$ |
| Lookup - **by value** | $O(n)$ |
| Insert - **at the beginning** | $O(1)$ |
| Insert - **at the end** | $O(1)$ |
| Insert - **in the middle** | $O(n)$ |
| Delete - **from the beginning**| $O(1)$ |
| Delete - **from the end** | $O(n)$ |
| Delete - **from the middle** | $O(n)$ |

---
#### Q: Create a Linked List is composed of the following methods:
- [x] [addFirst](#a-addfirst)
- [x] [addLast](#a-addlast)
- [x] [indexOf](#a-indexof)
- [x] [contains](#a-contains)
- [x] [removeFirst](#a-removefirst)
- [x] [removeLast](#a-removelast)
- [x] [toArray](#a-toarray)
- [x] [reverse ✸](#a-reverse)
- [x] [getKthFromTheEnd ✸](#a-getkthfromtheend)
- [x] [printMiddle ✸](#a-printmiddle)
- [x] [hasLoop ✸](#a-hasloop)

#### A: Structure of a linked list
```Java
public class LinkedList {
    private class Node {
        private int value;
        private Node next;

        public Node(int value) {
            this.value = value;
        }
    }

    private Node first;
    private Node last;
    private int size;
}
```
---
#### A: addFirst
```Java
private boolean isEmpty() {
    return first == null;
}

public void addFirst(int item) {
    var node = new Node(item);

    if (isEmpty()) {
        first = last = node;
    } else {
        node.next = first;
        first = node;
    }

    size++;
}
```
---
#### A: addLast
```Java
public void addLast(int item) {
    var node = new Node(item);

    if (isEmpty()) {
        first = last = node;
    } else {
        last.next = node;
        last = node;
    }

    size++;
}
```
---
#### A: indexOf
```Java
public int indexOf(int item) {
    int index = 0;
    var current = first;
    while (current != null) {
        if (current.value == item) 
            return index;

        current = current.next;
        index++;
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
#### A: removeFirst
```Java
public void removeFirst() {
    if (isEmpty())
        throw new NoSuchElementException();

    if (first == last) {
        first = last = null;
    } else {
        var second = first.next;
        first.next = null;
        first = second;
    }

    size--;
}
```
---
#### A: removeLast
```Java
private Node previous(Node node) {
    var current = first;
    while (current != null) {
        if (current.next == node) 
            return current;

        current = current.next;
    }

    return null;
}

public void removeLast() {
    if (isEmpty())
        throw new NoSuchElementException();

    if (first == last) {
      first = last = null;
    } else {
      var previous = previous(last);
      last = previous;
      last.next = null;
    }

    size--;
}
```
---
#### A: toArray
```Java
public int[] toArray() {
    int[] array = new int[size];

    var current = first;
    var index = 0;
    while (current != null) {
        array[index++] = current.value;
        current = current.next;
    }

    return array;
}
```

#### A: reverse
```Java
public void reverse() {
    if (isEmpty()) return;

    var previous = first;
    var current = first.next;
    while (current != null) {
      var next = current.next;
      current.next = previous;
      previous = current;
      current = next;
    }

    last = first;
    last.next = null;
    first = previous;
}
```
---
#### A: getKthFromTheEnd
```Java
public int getKthFromTheEnd(int k) {
    if (k < 1 || k > size)
        throw new IllegalStateException();

    if (isEmpty())
        throw new IllegalStateException();

    var a = first;
    var b = first;
    for (int i = 0; i < k - 1; i++)
        b = b.next;

    while(b != last) {
        b = b.next;
        a = a.next;
    }

    return a.value;
}
```
---
#### A: printMiddle
```Java
public void printMiddle() {
    if (isEmpty())
        throw new IllegalStateException();

    var a = first;
    var b = first;
    while (b != last && b.next != last) {
        b = b.next.next;
        a = a.next;
    }

    if (b == last) System.out.println(a.value);
    else System.out.println(a.value + ", " + a.next.value);
}
```
---
#### A: hasLoop
```Java
public boolean hasLoop() {
    var slow = first;
    var fast = first;

    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;

        if (slow == fast) 
            return true;
    }

    return false;
}
```