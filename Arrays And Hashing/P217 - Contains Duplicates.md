# P217 - Contains Duplicates
| Link                                                      | Tags        |
| --------------------------------------------------------- | ----------- |
| [p217](https://leetcode.com/problems/contains-duplicate/) | #easy #java |


## Optimal

| Runtime | Space  |
| ------- | ------ |
| $O(n)$  | $O(n)$ | 

```java
import java.util.Set;
import java.util.HashSet;

class Solution {
    public boolean containsDuplicate(int[] nums) {
    
        Set<Integer> S = new HashSet<Integer>();

        for (int number: nums){
            // Set.add returns false if element was already in the set
            if(!S.add(number))
                return true;
        }
        return false;
    }
}
```