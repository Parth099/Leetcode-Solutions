
# Easy Problems

## 125 - `valid-palindrome`

#easy 

Link: [Leetcode](https://leetcode.com/problems/valid-palindrome/solutions)
Runtime: $O(n)$

```python
import re
class Solution(object):

    def transform_alnum(self, s):
        return re.sub(r'[^a-zA-Z0-9]', '', s)

    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """

        s = self.transform_alnum(s).lower()

        if not s:
            return True

        left, right = 0, len(s) - 1

        while (left <= right):
            if s[left] != s[right]: return False

            left += 1; right -= 1

        return True
```

## 167 - `two-sum-ii`

#medium 

Link: [Leetcode](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/submissions/)
Runtime: $O(n)$

```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type numbers: List[int]
        :type target: int
        :rtype: List[int]
        """
        left, right = 0, len(nums) - 1

        while left < right:
            
            current = nums[left] + nums[right]

            if current < target:
                left  += 1
            elif current > target:
                right -= 1
            else: break

        return [left + 1, right + 1]
```

The array is presorted, the pointers on each side are moved to find the `target`.