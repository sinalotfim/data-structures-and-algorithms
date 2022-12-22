#### List of solutions can be resolved by Stack
- [x] [Given an integer K and a queue of integers, write code to reverse the order of the first K elements of the queue.](#q-given-an-integer-k-and-a-queue-of-integers-write-code-to-reverse-the-order-of-the-first-k-elements-of-the-queue)
- [x] [Build a stack using two queues.](#q-build-a-stack-using-two-queues)
- [x] [Build a priority queue.](#q-build-a-priority-queue)
---
##### Q: Given an integer K and a queue of integers, write code to reverse the order of the first K elements of the queue.
```Java
public class QueueReverser {
    public static void reverse(Queue<Integer> queue, int k) {
        if (k < 0 || k > queue.size())
            throw new IllegalArgumentException();

        var stack = new Stack<Integer>();
        for (int i = 0; i < k; i++)
            stack.push(queue.remove());

        while (!stack.empty())
            queue.add(stack.pop());

        for (int i = 0; i < queue.size() - k; i++)
            queue.add(queue.remove());
    }
}
```
---
##### Q: Build a stack using two queues.
```Java
public class StackWithTwoQueues {
    private Queue<Integer> mainQueue = new ArrayDeque<>();
    private Queue<Integer> tempQueue = new ArrayDeque<>();
    private int top;

    @Override
    public String toString() {
        return mainQueue.toString();
    }

    public void push(int item) {
        mainQueue.add(item);
        top = item;
    }

    public int pop() {
        if (isEmpty())
            throw new IllegalStateException();

        while (mainQueue.size() > 1) {
            top = mainQueue.remove();
            tempQueue.add(top);
        }

        swapQueues();

        return tempQueue.remove();
    }

    private void swapQueues() {
        var temp = mainQueue;
        mainQueue = tempQueue;
        tempQueue = temp;
    }

    public boolean isEmpty() {
        return mainQueue.isEmpty();
    }

    public int size() {
        return mainQueue.size();
    }

    public int peek() {
        if (isEmpty())
            throw new IllegalStateException();

        return top;
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
