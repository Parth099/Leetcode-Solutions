# P347 - Top K most Frequent Elements

| Link                                                           | Tags        |
| -------------------------------------------------------------- | ----------- |
| [p347](https://leetcode.com/problems/top-k-frequent-elements/) | #medium  #java |

## My Solution

```java
import java.util.Map;
import java.util.HashMap;

import java.util.PriorityQueue;

class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        // step 1 count the frequency of each element
        Map<Integer, Integer> Counter = new HashMap<>();

        for(int n: nums)
            Counter.put(n, Counter.getOrDefault(n, 0) + 1);

        
        // putting them in a max heap! (A)
        PriorityQueue<Map.Entry<Integer, Integer>> MaxHeap = new PriorityQueue<>((A, B) -> {
            return B.getValue() - A.getValue();
        });

        for (Map.Entry<Integer, Integer> entry : Counter.entrySet())
            MaxHeap.add(entry);

        // remove top k elemnents from heap and array them
        int[] result = new int[k];

        for(int i = 0; i < k; i++)
            result[i] = MaxHeap.poll().getKey();

        return result;
    }
}
```

The part `(A)` looks a bit confusing. 

The way priority works is that **bigger number** $\implies$ **higher priority**. Note, the comparator function should return a negative value if the first element should be placed before the second element in the heap. 

> Docs:
> `poll()`: Retrieves and removes the head of this queue, or returns `null` if this queue is empty.

## Alternative Solution
You can use a TreeMap and use a frequencies as a index:
```java
TreeMap<Integer, List<Integer>> freqMap = new TreeMap<>();
```