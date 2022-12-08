Q: Create an array with this methods
    1- insert
    2- insertAt
    3- removeAt
    4- indexOf
    5- reverse
    6- max
    7- intersect


A: Structure of an array
public class Array {
    private int[] items;
    private int count;

    public Array(length) {
        items = new int[length];
    }

    public void print() {
        for(int i = 0; i < count; i++)
            System.out.println(items[i]);
    }
}

A: insert method in an Array
private void resizeIfRequired() {
    if (items.length == count) {
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

A: insertAt method in an array
public void insertAt(int item, int index) {
    if (index < 0 || index > count)
        throw new IllegalArgumentException();

    resizeIfRequired();

    for (int i = count - 1; i >= index; i--)
      items[i + 1] = items[i];

    items[index] = item;
    count++;
}

A: removeAt method in an array
public void removeAt(int index) {
    if (index < 0 || index >= count)
        throw new IllegalArgumentException();

    for (int i = index; i < count; i++)
        items[i] = items[i + 1];

    count--;
}

A: indexOf method in an array
public int indexOf(int item) {
    for (int i = 0; i < count; i++)
        if (items[i] == item)
            return i;

    return -1;
}

A: reverse method in an array
public void reverse() {
    int[] newItems = new int[count];

    for (int i = 0; i < count; i++)
        newItems[i] = items[count - i - 1];

    items = newItems;
}

A: max method in an array
public int max() {
    int max = 0;
    for (int item : items)
        if (item > max)
            max = item;

    return max;
}

A: intersect method in an array
public Array intersect(Array other) {
    var intersection = new Array(count);

    for (int item : items)
        if (other.indexOf(item) >= 0)
            intersection.insert(item);

    return intersection;
}

