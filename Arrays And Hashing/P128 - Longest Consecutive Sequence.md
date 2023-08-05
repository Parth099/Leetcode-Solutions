# P128 - Longest Consecutive Sequence
| Link                                                 | Tags          |
| ---------------------------------------------------- | ------------- |
| [p128](https://leetcode.com/problems/longest-consecutive-sequence/) | #medium #java | 

## Optimal Solution

| Runtime | Space  |
| ------- | ------ |
| $O(n)$  | $O(n)$ | 

```python
class Solution:
    def longestConsecutive(self, nums):

        if len(nums) < 2:
            return len(nums)

        num_set = set(nums)
        max_len = 1

        for num in nums:
            # ensure you are not starting a streak at the wrong locatin
            if num - 1 not in num_set:
            
                length = 1
                
                while num + length in  num_set: length += 1

                max_len = max(max_len, length)

        return max_len

```

Should be readable. 