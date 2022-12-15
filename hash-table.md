#### Q: Create a hash table is comprising the following methods:
- [x] [put](#a-put)
- [x] [remove](#a-remove)
- [x] [get](#a-get)

---
##### A: Structure of a hash table
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
##### A: put
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
    var bucket = entries[index];
    if (bucket == null)
        entries[index] = new LinkedList<>();

    return bucket;
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
##### A: remove
```Java
ppublic void remove(int key) {
    var entry = getEntry(key);
    if (entry == null)
        throw new IllegalStateException();
    
    getBucket(key).remove(entry);
  }
```
---
##### A: get
```Java 
public String get(int key) {
    var entry = getEntry(key);

    return entry == null ? null : entry.value;
}
```