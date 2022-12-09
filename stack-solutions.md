#### List of solutions can be resolved by Stack
- [x] [Reverse a string](#q-reverse-a-string)
- [x] [Create a balanced expression](#q-create-a-balanced-expression)
- [x] [Design a stack that supports push, pop and retrieving the minimum value in constant time.](#q-design-a-stack-that-supports-push-pop-and-retrieving-the-minimum-value-in-constant-time)
---
##### Q: Reverse a string
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
##### Q: Create a balanced expression
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
---
##### Q: Design a stack that supports push, pop and retrieving the minimum value in constant time
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