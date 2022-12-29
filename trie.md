#### Q: Create a Trie is comprising the following methods:
- [x] [insert](#a-insert)
- [x] [contains](#a-contains)
- [x] [remove](#a-remove)
- [x] [traverse](#a-traverse)
- [x] [findWords](#a-findwords)
- [x] [containRecursive](#a-containrecursive)
- [x] [countWords](#a-countwords)
- [x] [printWords](#a-printwords)
- [x] [longestCommonPrefix](#a-longestcommonprefix)

#### A: Structure of a Trie
```Java
public class Trie {
    public static int ALPHABET_SIZE = 26;

    private class Node {
        private char value;
        private HashMap<Character, Node> children = new HashMap<>();
        private boolean isEndOfWord;

        public Node(char value) {
            this.value = value;
        }

        @Override
        public String toString() {
            return "value=" + value;
        }

        public boolean hasChild(char ch) {
            return children.containsKey(ch);
        }

        public void addChild(char ch) {
            children.put(ch, new Node(ch));
        }

        public Node getChild(char ch) {
            return children.get(ch);
        }

        public Node[] getChildren() {
            return children.values().toArray(new Node[0]);
        }

        public boolean hasChildren() {
            return !children.isEmpty();
        }

        public void removeChild(char ch) {
            children.remove(ch);
        }
    }

    private Node root = new Node(' ');
}
```
---
#### A: insert
```Java
public void insert(String word) {
    var current = root;
    for (var ch : word.toCharArray()) {
        if (!current.hasChild(ch))
            current.addChild(ch);
        current = current.getChild(ch);
    }

    current.isEndOfWord = true;
}
```
---
#### A: contains
```Java
public boolean contains(String word) {
    if (word == null)
        return false;

    var current = root;
    for (var ch : word.toCharArray()) {
        if (!current.hasChild(ch))
            return false;
        current = current.getChild(ch);
    }

    return current.isEndOfWord;
}
```
---
#### A: remove
```Java
public void remove(String word) {
    if (word == null)
        return;

    remove(root, word, 0);
}

private void remove(Node root, String word, int index) {
    if (index == word.length()) {
        root.isEndOfWord = false;
        return;
    }

    var ch = word.charAt(index);
    var child = root.getChild(ch);
    if (child == null)
        return;

    remove(child, word, index + 1);

    if (!child.hasChildren() && !child.isEndOfWord)
        root.removeChild(ch);
}
```
---
#### A: traverse
```Java
public void traverse() {
    traverse(root);
}

private void traverse(Node root) {
    for (var child : root.getChildren())
        traverse(child);

    // Post-order: visit the root last
    System.out.println(root.value);
}

private void traverse(Node root) {
    // Pre-order: visit the root first
    System.out.println(root.value);

    for (var child : root.getChildren())
        traverse(child);
}
```
---
#### A: findWords
```Java
private Node findLastNodeOf(String prefix) {
    if (prefix == null)
        return null;

    var current = root;
    for (var ch : prefix.toCharArray()) {
        var child = current.getChild(ch);
        if (child == null)
            return null;
        
        current = child;
    }
    
    return current;
}

public List<String> findWords(String prefix) {
    List<String> words = new ArrayList<>();
    var lastNode = findLastNodeOf(prefix);
    findWords(lastNode, prefix, words);

    return words;
}

private void findWords(Node root, String prefix, List<String> words) {
    if (root == null)
      return;

    if (root.isEndOfWord)
      words.add(prefix);

    for (var child : root.getChildren())
      findWords(child, prefix + child.value, words);
}
```
---
#### A: containRecursive
```Java
public boolean containsRecursive(String word) {
    if (word == null)
        return false;

    return containsRecursive(root, word, 0);
}

private boolean containsRecursive(Node root, String word, int index) {
    if (index == word.length())
        return root.isEndOfWord;

    if (root == null)
        return false;

    var ch = word.charAt(index);
    var child = root.getChild(ch);
    if (child == null)
        return false;

    return containsRecursive(child, word, index + 1);
}
```
---
#### A: countWords
```Java
public int countWords() {
    return countWords(root);
}

private int countWords(Node root) {
    var total = 0;

    if (root.isEndOfWord)
        total++;

    for (var child : root.getChildren())
        total += countWords(child);

    return total;
}
```
---
#### A: printWords
```Java
public void printWords() {
    printWords(root, "");
}

private void printWords(Node root, String word) {
    if (root.isEndOfWord)
        System.out.println(word);

    for (var child : root.getChildren())
        printWords(child, word + child.value);
}
```
---
#### A: longestCommonPrefix
```Java
public static String longestCommonPrefix(String[] words) {
    if (words == null)
        return "";

    var trie = new Trie();
    for (var word : words)
        trie.insert(word);

    var prefix = new StringBuffer();
    var maxChars = getShortest(words).length();
    var current = trie.root;
    while (prefix.length() < maxChars) {
        var children = current.getChildren();
        if (children.length != 1)
            break;
      
        current = children[0];
        prefix.append(current.value);
    }

    return prefix.toString();
}

private static String getShortest(String[] words) {
    if (words == null || words.length == 0)
        return "";

    var shortest = words[0];
    for (var i = 1; i < words.length; i++) {
        if (words[i].length() < shortest.length())
            shortest = words[i];
    }

    return shortest;
}
```