# P242 - Valid Anagram

| Link                                                 | Tags        |
| ---------------------------------------------------- | ----------- |
| [p242](https://leetcode.com/problems/valid-anagram/) | #easy #java |

## My Solution

| Runtime | Space  |
| ------- | ------ |
| $O(n)$  | $O(n)$ | 


```java
import java.util.HashMap;
import java.util.Map;

import java.util.function.BiFunction;  

class Solution {

    // helper to take string to map
    public Map<Character, Integer> stringToMap(String s){
        // map to be returned
        Map<Character, Integer> M = new HashMap<>();

        // key computing function, if it exists increment, if not start at 1
        BiFunction <Character, Integer, Integer> computeFn = (key, storedValue) -> (storedValue == null) ? 1 : storedValue + 1;

        // apply counting function to each letter
        for(int i = 0, n = s.length() ; i < n ; i++) { 
            M.compute(s.charAt(i), computeFn);
        }

        return M;
    }

    public boolean isAnagram(String s, String t) {
        
        Map<Character, Integer> SMap = this.stringToMap(s);
        Map<Character, Integer> TMap = this.stringToMap(t);

        // compare internal maps
        return SMap.entrySet().equals(TMap.entrySet());
    }
}
```

It uses two `HashSet`s and compares to check if they contain the same entries. 

## Smarter Solution

| Runtime | Space  |
| ------- | ------ |
| $O(n)$  | $O(n)$ | 

```java
import java.util.Optional;

class Solution {
    public boolean isAnagram(String s, String t) {
        Map<Integer, Integer> M = new HashMap<>();

        // push up on all used letters by s
        s.chars().forEach(chr -> M.put(chr, M.getOrDefault(chr, 0) + 1));

        // push down on all letters present in t
        t.chars().forEach(chr -> M.put(chr, M.getOrDefault(chr, 0) - 1));

        // each and every value should be 0
        return M.values().stream().allMatch(v -> v == 0);
    }
}
```