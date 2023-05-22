# P49 - Group Anagram
| Link                                                 | Tags          |
| ---------------------------------------------------- | ------------- |
| [p49](https://leetcode.com/problems/group-anagrams/) | #medium #java | 


## Optimal

| Runtime                                              | Space  |
| ---------------------------------------------------- | ------ |
| $O(n*m \log m)$ where $m$ is the length of the words | $O(n)$ |


```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> AnagramMap = new HashMap<>();

        for(String str: strs){
            // find sorted representation of word
            char[] charArray = str.toCharArray();
            Arrays.sort(charArray);
            String sorted = new String(charArray); 

            // create a box if not present already
            AnagramMap.putIfAbsent(sorted, new ArrayList<String>());
            AnagramMap.get(sorted).add(str);
        }

        // map to list for return
        List<List<String>> AnagramGroupings = new ArrayList<List<String>>();
        AnagramMap.forEach((letters, group) -> {
            AnagramGroupings.add(group);
        });

        return AnagramGroupings;
    }
}
```

The approach is to create boxes in the `Map` where the key is each letter present in the word. Since they sorted string of each anagram is the same, it is used as the key. 