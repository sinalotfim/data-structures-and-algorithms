#### List of solutions can be resolved by Stack
- [x] [Given an integer K and a queue of integers, write code to reverse the order of the first K elements of the queue.](#q-given-an-integer-k-and-a-queue-of-integers-write-code-to-reverse-the-order-of-the-first-k-elements-of-the-queue)
- [x] [Build a queue using a linked list from scratch.](#q-build-a-queue-using-a-linked-list-from-scratch)
- [x] [Build a stack using two queues.](#q-build-a-stack-using-two-queues)
- [x] [Build a priority queue.](#q-build-a-priority-queue)
---
##### Q: Given an integer K and a queue of integers, write code to reverse the order of the first K elements of the queue.
```Java
public class QueueReverser {
    public static void reverse(Queue<Integer> queue, int k) {
        if (k < 0 || k > queue.size())
            throw new IllegalArgumentException();

        Stack<Integer> stack = new Stack<>();

        // Dequeue the first K elements from the queue
        // and push them onto the stack
        for (int i = 0; i < k; i++)
            stack.push(queue.remove());

        // Enqueue the content of the stack at the
        // back of the queue
        while (!stack.empty())
            queue.add(stack.pop());

        // Add the remaining items in the queue (items
        // after the first K elements) to the back of the
        // queue and remove them from the beginning of the queue
        for (int i = 0; i < queue.size() - k; i++)
            queue.add(queue.remove());
    }
}
```
---
##### Q: Build a queue using a linked list from scratch.
```Java
public class LinkedListQueue {
    private class Node {
        private int value;
        private Node next;

        public Node(int value) {
            this.value = value;
        }
    }

    private Node head;
    private Node tail;
    private int count;

    public void enqueue(int item) {
        var node = new Node(item);

        if (isEmpty())
            head = tail = node;
        else {
            tail.next = node;
            tail = node;
        }

        count++;
    }

    public int dequeue() {
        if (isEmpty())
            throw new IllegalStateException();

        int value;
        if (head == tail) {
            value = head.value;
            head = tail = null;
        }
        else {
            value = head.value;
            var second = head.next;
            head.next = null;
            head = second;
        }

        count--;

        return value;
    }

    public int peek() {
        if (isEmpty())
            throw new IllegalStateException();

        return head.value;
    }

    public int size() {
        return count;
    }

    public boolean isEmpty() {
        return head == null;
    }

    public String toString() {
        ArrayList<Integer> list = new ArrayList<>();

        Node current = head;
        while (current != null) {
            list.add(current.value);
            current = current.next;
        }

        return list.toString();
    }
}
```
---
##### Q: Build a stack using two queues.
```Java
public class QueueWithTwoStacks {
    private Stack<Integer> stack1 = new Stack<>();
    private Stack<Integer> stack2 = new Stack<>();

    public void enqueue(int item) {
        stack1.push(item);
    }

    public int dequeue() {
        if (isEmpty()) throw new IllegalStateException();

        moveStack1ToStack2();

        return stack2.pop();
    }

    private void moveStack1ToStack2() {
        if (stack2.isEmpty())
            while (!stack1.isEmpty())
                stack2.push(stack1.pop());
    }

    public int peek() {
        if (isEmpty()) throw new IllegalStateException();

        moveStack1ToStack2();

        return stack2.peek();
    }

    public boolean isEmpty() {
        return stack1.isEmpty() && stack2.isEmpty();
    }
}
```
---
##### Q: Build a priority queue
```Java
public class PriorityQueue {
    private int[] items = new int[5];
    private int count;

    @Override
    public String toString() {
        return Arrays.toString(items);
    }

    public void add(int item) {
        if (isFull()) throw new IllegalStateException();

        var i = shiftItemsToInsert(item);
        items[i] = item;
        count++;
    }

    public boolean isFull() {
        return count == items.length;
    }

    private int shiftItemsToInsert(int item) {
        int i;
        for (i = count - 1; i >= 0; i--) {
            if (items[i] > item)
                items[i + 1] = items[i];
            else
                break;
        }
    
        return i + 1;
    }

    public int remove() {
        if (isEmpty())
            throw new IllegalStateException();

        return items[--count];
    }

    public boolean isEmpty() {
        return count == 0;
    }
}
```
