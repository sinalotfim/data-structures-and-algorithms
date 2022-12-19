#### List of solutions can be resolved by Stack
- [x] [Implement two stacks in one array](#implement-two-stacks-in-one-array)
- [x] [Design a stack that supports push, pop and retrieving the minimum value in constant time.](#q-design-a-stack-that-supports-push-pop-and-retrieving-the-minimum-value-in-constant-time)
- [x] [Reverse a string](#q-reverse-a-string)
- [x] [Create a balanced expression](#q-create-a-balanced-expression)
---
#### Implement two stacks in one array
```Java
public class TwoStacks {
    private int top1;
    private int top2;
    private int[] items;

    public TwoStacks(int capacity) {
        if (capacity <= 0)
            throw new IllegalArgumentException("capacity must be 1 or greater.");

        items = new int[capacity];
        top1 = -1;
        top2 = capacity;
    }

    // First Stack
    public boolean isFull1() {
        return top1 + 1 == top2;
    }

    public void push1(int item) {
        if (isFull1())
            throw new IllegalStateException();

        items[++top1] = item;
    }

    public boolean isEmpty1() {
        return top1 == -1;
    }

    public int pop1() {
        if (isEmpty1())
            throw new IllegalStateException();

        return items[top1--];
    }

    // Second Stack
    public boolean isFull2() {
        return top2 - 1 == top1;
    }

    public void push2(int item) {
        if (isFull2())
            throw new IllegalStateException();

        items[--top2] = item;
    }

    public boolean isEmpty2() {
        return top2 == items.length;
    }

    public int pop2() {
        if (isEmpty2())
            throw new IllegalStateException();

        return items[top2++];
    }

    @Override
    public String toString() {
        return Arrays.toString(items);
    }
}

```
---
#### Q: Design a stack that supports push, pop and retrieving the minimum value in constant time
```Java
public class MinStack {
    private Stack stack = new Stack();
    private Stack minStack = new Stack();

    public void push(int item) {
        stack.push(item);

        if (minStack.isEmpty()) minStack.push(item);
        else if (item < minStack.peek())minStack.push(item);
    }

    public int pop() {
        if (stack.isEmpty()) throw new IllegalStateException();

        var top = stack.pop();
        if (minStack.peek() == top) minStack.pop();

        return top;
    }

    public int min() {
        return minStack.peek();
    }
}
```
---
#### Q: Reverse a string
```Java
public class StringReverser {
    public String reverse(String input) {
        if (input == null)
            throw new IllegalArgumentException();

        Stack<Character> stack = new Stack<>();

        for (char ch : input.toCharArray())
            stack.push(ch);

        StringBuffer reversed = new StringBuffer();
        while (!stack.empty())
            reversed.append(stack.pop());

        return reversed.toString();
    }
}
```
---
#### Q: Create a balanced expression
```Java
public class Expression {
    private final List<Character> leftBrackets = Arrays.asList('(', '<', '[', '{');
    private final List<Character> rightBrackets = Arrays.asList(')', '>', ']', '}');

    public boolean isBalanced(String input) {
        Stack<Character> stack = new Stack<>();

        for (char ch : input.toCharArray()) {
            if (isLeftBracket(ch))
                stack.push(ch);

            if (isRightBracket(ch)) {
                if (stack.empty()) return false;

                var top = stack.pop();
                if (!bracketsMatch(top, ch)) return false;
            }
        }

        return stack.empty();
    }

    private boolean isLeftBracket(char ch) {
        return leftBrackets.contains(ch);
    }

    private boolean isRightBracket(char ch) {
        return rightBrackets.contains(ch);
    }

    private boolean bracketsMatch(char left, char right) {
        return leftBrackets.indexOf(left) == rightBrackets.indexOf(right);
    }
}
```