#### Binary Search Tree

-   Binary Search Tree is a data structure that quickly allows us to **maintain a sorted list of numbers**.

    1. It is called a **Binary Tree** because each tree node has a **maximum of two children**.
    2. It is called a **Search Tree** because it **can be used to search** for the presence of a number in <mark>$O(\log n)$</mark> time.

-   **Left** Node **<** **Root** Node **<** **Right** Node.
-   The properties that separate a Binary Search Tree from a regular Binary Tree is

    1. All nodes of **left subtree** are **less than** the root node.
    2. All nodes of **right subtree** are **more than** the root node.
    3. **Both subtrees** of each node are also **BSTs** i.e. they have the above two properties.

    ![Binary search tree](../assets/binary-search-tree.webp)

-   Applications
    1.  Binary Search Trees (BSTs) are used to quickly check whether an element is present in a set or not.
    2.  In **multilevel indexing** in the database
    3.  For dynamic sorting
    4.  For managing virtual memory areas in Unix kernel

| Time Complexity |             |              |            |
| :-------------- | :---------: | :----------: | :--------: |
| Operation       |  Best Case  | Average Case | Worst Case |
| Lookup          | $O(\log n)$ | $O(\log n)$  |   $O(n)$   |
| Insert          | $O(\log n)$ | $O(\log n)$  |   $O(n)$   |
| Delete          | $O(\log n)$ | $O(\log n)$  |   $O(n)$   |

| Space Complexity |            |
| :--------------- | :--------: |
| Operation        | Worst Case |
| Lookup           |   $O(n)$   |
| Insert           |   $O(n)$   |
| Delete           |   $O(n)$   |

#### Q: Create a Binary Search Tree is composed of the following methods:

-   [x] [structure](#a-structure-of-a-binary-search-tree)
-   [x] [contains](#a-contains)
-   [x] [min ✸](#a-min)
-   [x] [max ✸](#a-max)

###### The rest methods are available and are the same with Binary Tree methods

-   [ ] [insert](./binary-tree.md#a-insert)
-   [ ] [pre-order](./binary-tree.md#a-pre-order)
-   [ ] [in-order](./binary-tree.md#a-in-order-asc) - ASC
-   [ ] [in-order](./binary-tree.md#a-in-order-desc) - DESC
-   [ ] [post-order](./binary-tree.md#a-post-order)
-   [ ] [height ✸](./binary-tree.md#a-height)
-   [ ] [equals ✸](./binary-tree.md#a-equals)
-   [ ] [isBST ✸](./binary-tree.md#a-isbst)
-   [ ] [getNodesAtDistance ✸](./binary-tree.md#a-getnodesatdistance)
-   [ ] [level-order ✸](./binary-tree.md#a-level-order)
-   [ ] [size ✸](./binary-tree.md#a-size)
-   [ ] [countLeaves ✸](./binary-tree.md#a-countleaves)
-   [ ] [isBalanced ✸](./binary-tree.md#a-isbalanced)
-   [ ] [isPerfect ✸](./binary-tree.md#a-isperfect)
-   [ ] [areSibling ✸](./binary-tree.md#a-aresibling)
-   [ ] [getAncestors ✸](./binary-tree.md#a-getancestors)

---

#### A: Structure of a Binary Search Tree

```Java
public class BinarySearchTree {
    private class Node {
        private int value;
        private Node leftChild;
        private Node rightChild;

        public Node(int value) {
            this.value = value;
        }

        @Override
        public String toString() {
            return "Node: " + value;
        }
    }

    private Node root;
}
```

---

#### A: contains

```Java
public boolean contains(int value) {
    var current = root;
    while (current != null) {
        if (value < current.value)
            current = current.leftChild;
        else if (value > current.value)
            current = current.rightChild;
        else
            return true;
    }

    return false;
}
```

---

#### A: min

```Java
// O(log n)
// Method 1
public int min() {
    if (root == null)
        throw new IllegalStateException();

    return min(root);
}

private int min(Node root) {
    if (root.leftChild == null)
        return root.value;

    return min(root.leftChild);
}

// O(log n)
// Method 2
public int min() {
    if (root == null)
        throw new IllegalStateException();

    var current = root;
    var last = current;
    while (current != null) {
        last = current;
        current = current.leftChild;
    }

    return last.value;
}
```

---

#### A: max

```Java
// O(log n)
// Method 1
public int max() {
    if (root == null)
        throw new IllegalStateException();

    return max(root);
}

private int max(Node root) {
    if (root.rightChild == null)
        return root.value;

    return max(root.rightChild);
}

// O(log n)
// Method 2
public int max() {
    if (root == null)
        throw new IllegalStateException();

    var current = root;
    var last = current;
    while (current != null) {
        last = current;
        current = current.rightChild;
    }

    return last.value;
}
```
