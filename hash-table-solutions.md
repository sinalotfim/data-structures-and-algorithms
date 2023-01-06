#### List of solutions can be resolved by Stack
- [x] [Find first repeated character](#q-find-first-repeated-character)
- [x] [Find first non-repeated character.](#q-find-first-non-repeated-character)
- [x] [Find the most repeated element in an array of integers.](#q-find-the-most-repeated-element-in-an-array-of-integers)
- [x] [Given an array of integers, count the number of unique pairs of integers that have difference k.](#q-given-an-array-of-integers-count-the-number-of-unique-pairs-of-integers-that-have-difference-k)
- [x] [Given an array of integers, return indices of the two numbers such that they add up to a specific target.](#q-given-an-array-of-integers-return-indices-of-the-two-numbers-such-that-they-add-up-to-a-specific-target)
---
#### Q: Find first repeated character.
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
#### Q: Find first non-repeated character.
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
#### Q: Find the most repeated element in an array of integers.
```Java
public int mostFrequent(int[] numbers) {
    Map<Integer, Integer> map = new HashMap<>();
    for (var number : numbers) {
        var count = map.getOrDefault(number, 0);
        map.put(number, count + 1);
    }

    int out = numbers[0];
    int max = map.get(result);
    for (var item : map.entrySet()) {
        if (item.getValue() > max) {
            max = item.getValue();
            out = item.getKey();
        }
    }

    return out;
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
        if (set.contains(number + difference)) count++;
        if (set.contains(number - difference)) count++;
        
        set.remove(number);
    }


    return count;
}
```
---
#### Q: Given an array of integers, return indices of the two numbers such that they add up to a specific target.
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
