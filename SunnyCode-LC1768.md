# LC 1768

## Basic
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

## More Creative

```python
class Solution:
    def mergeAlternately(self, s1: str, s2: str) -> str:
        
        # make s1 the longer string
        if len(s1) < len(s2):
            s1, s2 = s2, s1 # swap strings

        s1_leftover = s1[len(s2):] # find whats gonna be left over when merged

        zipped = zip(s1, s2)
        result = "".join(f'{item[0]}{item[1]}'  for item in zipped) # use zip to split and merge

        return result + s1_leftover
```

## `itertools`

```python
from itertools import zip_longest

class Solution:
    def mergeAlternately(self, s1: str, s2: str) -> str:
        zipped = zip_longest(s1, s2, fillvalue="")
        return "".join(f'{item[0]}{item[1]}'  for item in zipped)
```
