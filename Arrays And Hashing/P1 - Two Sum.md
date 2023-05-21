# P1 - Two Sum
| Link                                         | Tags        |
| -------------------------------------------- | ----------- |
| [p1](https://leetcode.com/problems/two-sum/) | #easy #java |


<!--
## Two Pointer
| Runtime       | Space  |
| ------------- | ------ |
| $O(n \log n)$ | $O(1)$ |
-->

## Hashmap
| Runtime | Space  |
| ------- | ------ |
| $O(n)$  | $O(n)$ | 

```java
import java.util.Map;
import java.util.HashMap;


class Solution {
    public int[] twoSum(int[] nums, int target) {

        // save whats needed to get to target and what index its at
        Map<Integer, Integer> Targets = new HashMap<>();

        for(int i = 0; i < nums.length; i++){
            // if the current numbers comlement exists return it
            if(Targets.containsKey(nums[i]))
                return new int[]{Targets.get(nums[i]), i};

            // save complement
            Targets.put(target - nums[i], i);
        }

        // error state
        return new int[]{-1, -1};
    }
}
```
