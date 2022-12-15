#### List of solutions can be resolved by Stack
- [x] [First repeated character](#q-first-repeated-character)
- [x] [First non-repeated character.](#q-first-non-repeated-character)
- [x] [Find the most repeated element in an array of integers.](#q-find-the-most-repeated-element-in-an-array-of-integers)
- [x] [Given an array of integers, count the number of unique pairs of integers that have difference k.](#q-given-an-array-of-integers-count-the-number-of-unique-pairs-of-integers-that-have-difference-k)
- [x] [Given an array of integers, return indices of the two numbers such that they add up to a specific target.](#q-given-an-array-of-integers-return-indices-of-the-two-numbers-such-that-they-add-up-to-a-specific-target)
- [x] [Build a hash table from scratch.](#q-build-a-hash-table-from-scratch)
---
##### Q: First repeated character.
```Java
public char findFirstRepeatedChar(String str) {
    Set<Character> set = new HashSet<>();

    for (var ch : str.toCharArray()) {
        if (set.contains(ch))
            return ch;

        set.add(ch);
    }

    return Character.MIN_VALUE;
}
```
---
##### Q: First non-repeated character.
```Java
 public char findFirstNonRepeatingChar(String str) {
    Map<Character, Integer> map = new HashMap<>();

    var chars = str.toCharArray();
    for (var ch : chars) {
        var count = map.containsKey(ch) ? map.get(ch) : 0;
        map.put(ch, count + 1);
    }

    for (var ch : chars)
        if (map.get(ch) == 1)
            return ch;

    return Character.MIN_VALUE;
}

```
---
##### Q: Find the most repeated element in an array of integers.
```Java
public int mostFrequent(int[] numbers) {
    Map<Integer, Integer> map = new HashMap<>();
    for (var number : numbers) {
        var count = map.getOrDefault(number, 0);
        map.put(number, count + 1);
    }

    int max = -1;
    int result = numbers[0];
    for (var item : map.entrySet()) {
        if (item.getValue() > max) {
            max = item.getValue();
            result = item.getKey();
        }
    }

    return result;
}
```
---
##### Q: Given an array of integers, count the number of unique pairs of integers that have difference k.
```Java
public int countPairsWithDiff(int[] numbers, int difference) {
    Set<Integer> set = new HashSet<>();
    for (var number : numbers)
        set.add(number);

    var count = 0;
    for (var number : numbers) {
        if (set.contains(number + difference))
            count++;
        if (set.contains(number - difference))
            count++;
        
        set.remove(number);
    }


    return count;
}
```
---
##### Q: Given an array of integers, return indices of the two numbers such that they add up to a specific target.
```Java
public int[] twoSum(int[] numbers, int target) {
    Map<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < numbers.length; i++) {
        int complement = target - numbers[i];
        if (map.containsKey(complement)) {
            return new int[] { map.get(complement), i };
        }
        map.put(numbers[i], i);
    }

    return null;
}
```
---
#### Q: Build a hash table from scratch.
```java
public class HashMap {
    private class Entry {
        private int key;
        private String value;

        public Entry(int key, String value) {
            this.key = key;
            this.value = value;
        }

        @Override
        public String toString() {
            return value;
        }
    }

    private Entry[] entries = new Entry[5];
    private int count;

    public void put(int key, String value) {
        var entry = getEntry(key);
        if (entry != null) {
            entry.value = value;
            return;
        }

        if (isFull())
            throw new IllegalStateException();

        entries[getIndex(key)] = new Entry(key, value);
        count++;
    }

    public String get(int key) {
        var entry = getEntry(key);
        return entry != null ? entry.value : null;
    }

    public void remove(int key) {
        var index = getIndex(key);
        if (index == -1 || entries[index] == null)
            return;

        entries[index] = null;
        count--;
    }

    public int size() {
        return count;
    }

    private Entry getEntry(int key) {
        var index = getIndex(key);
        return index >= 0 ? entries[index] : null;
    }

    private int getIndex(int key) {
        int steps = 0;
        while (steps < entries.length) {
            int index = index(key, steps++);
            var entry = entries[index];
            if (entry == null || entry.key == key)
                return index;
        }

        return -1;
    }

    private boolean isFull() {
        return count == entries.length;
    }

    private int index(int key, int i) {
        return (hash(key) + i) % entries.length;
    }

    private int hash(int key) {
        return key % entries.length;
    }

    @Override
    public String toString() {
        return Arrays.toString(entries);
    }
}

```
