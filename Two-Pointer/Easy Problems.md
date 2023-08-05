
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