
# 11 - Container With Most Water

| Link                                         | Tags        |
| -------------------------------------------- | ----------- |
| [p11](https://leetcode.com/problems/container-with-most-water/) | #medium  #python  |


# Optimal Solution

| Runtime | Space  |
| ------- | ------ |
| $O(n)$  | $O(1)$ | 

```python
class Solution:
    def maxArea(self, heights: List[int]) -> int:

        result = 0
        left, right = 0, len(heights) - 1

        while left < right:
            area = (right - left) * min(heights[left], heights[right])
            result = max(result, area)

			# move left since right height is already higher
            if heights[left] < heights[right]:
                left  += 1
            else: 
                right -= 1

        return result

```


