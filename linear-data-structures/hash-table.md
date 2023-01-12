#### Hash Tables
- store **key/value pairs**
- Collision solving
    - Chaining
    - Open adressing
- Usings
    - Spell checkers
    - Dictionaries
    - Compilers
    - Code Editors
- Languages
    - Java &rarr; HashMap
    - C# &rarr; Dictionary
    - Python &rarr; Dictionary
    - JavaScript &rarr; Object

| Operation | Approximation |
| :--- | :---: |
| Lookup | $O(1)$ |
| Insert | $O(1)$ |
| Delete | $O(1)$ |

---
#### Q: Create a `Hash Table` is composed of the following methods:
- [x] [put](#a-put)
- [x] [get](#a-get)
- [x] [remove](#a-remove)

---
#### A: Structure of a hash table
```Java
public class HashTable {
    private class Entry {
        private int key;
        private String value;

        public Entry(int key, String value) {
            this.key = key;
            this.value = value;
        }
    }

    private LinkedList<Entry>[] entries = new LinkedList[5];
}
```
---
#### A: put
```Java
private int hash(int key) {
    return key % entries.length;
}

private LinkedList<Entry> getBucket(int key) {
    return entries[hash(key)];
}

private Entry getEntry(int key) {
    var bucket = getBucket(key);
    if (bucket != null) {
        for (var entry : bucket) {
            if (entry.key == key)
                return entry;
        }
    }

    return null;
}

private LinkedList<Entry> getOrCreateBucket(int key) {
    var index = hash(key);
    if (entries[index] == null)
        entries[index] = new LinkedList<Entry>();
        
    return entries[index];
}

public void put(int key, String value) {
    var entry = getEntry(key);
    if (entry != null) {
        entry.value = value;
        return;
    }

    getOrCreateBucket(key).add(new Entry(key, value));
}
```
---
#### A: get
```Java 
public String get(int key) {
    var entry = getEntry(key);

    return entry == null ? null : entry.value;
}
```
---
#### A: remove
```Java
public void remove(int key) {
    var entry = getEntry(key);
    if (entry == null)
        throw new IllegalStateException();
    
    getBucket(key).remove(entry);
}
```