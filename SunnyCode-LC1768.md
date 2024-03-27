```python
class Solution:
    def mergeAlternately(self, s1: str, s2: str) -> str:
    
        length_s1 = len(s1)
        length_s2 = len(s2)

        len_largest = max(length_s1, length_s2) # get largest string
        current_index = 0 # index to where we are now in the strings

        result = ""

        while current_index < len_largest:

            if current_index < length_s1: # check if we reached the end of s1
                result += s1[current_index]

            if current_index < length_s2: # check if we reached the end of s2
                result += s2[current_index]

            current_index += 1 # move onto next letter
  
        return result
```
