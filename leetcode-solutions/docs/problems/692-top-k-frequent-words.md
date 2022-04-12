---
tags:
    - Array
    - Hash Table
    - Divide and Conquer
    - Sorting
    - Heap (Priority Queue)
    - Bucket Sort
    - Counting
    - Quick Select
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/){:target="\_blank"}

**Approach 1 : Using Heap (PriorityQueue)**

=== "Java"

    ``` java
    class Solution {
        public List<String> topKFrequent(String[] words, int k) {

            List<String> result = new ArrayList<String>();
            HashMap<String, Integer> map = new HashMap<String, Integer>();

            // MaxHeap to store the strings based on their frequency
            Queue<String> heap =
                            new PriorityQueue<String>(
                                (e1, e2) -> map.get(e1) == map.get(e2) ?
                                    e1.compareTo(e2) : map.get(e2) - map.get(e1));

            // Hashmap which stores (element, frequency)
            for(String str: words)
                map.put(str, map.getOrDefault(str, 0) + 1);

            // Add the unique elements of HashMap to Maxheap
            for(String str: map.keySet())
                heap.add(str);

            // Add the top 'k' frequent strings from heap into the result
            while(k-- > 0)
                result.add(heap.poll());

            return result;
        }
    }
    ```

-   [x] **Time Complexity :** O(n\*log n) where _n_ is the length of array

-   [x] **Space Complexity :** O(n) where _n_ is the length of array

<hr>

**Approach 2 : HashMap + Sorting**

=== "Java"

    ```java
    class Solution {
        public List<String> topKFrequent(String[] words, int k) {

            List<String> result = new ArrayList<String>();
            HashMap<String,Integer> map = new HashMap<String,Integer>();

            // Hashmap which stores (element, frequency)
            for(String str: words)
                map.put(str, map.getOrDefault(str, 0) + 1);

            // Create a list from the map
            List<Map.Entry<String, Integer>> list =
                new LinkedList<Map.Entry<String, Integer>>(map.entrySet());

            // Sort the list using lambda expression
            Collections.sort(list, (e1,e2) -> e1.getValue() == e2.getValue() ?
                                            e1.getKey().compareTo(e2.getKey()) : e2.getValue() - e1.getValue());

            // put elements from sorted list to the result array
            int i = 0;
            for (Map.Entry<String, Integer> itr : list) {
                result.add(itr.getKey());
                if(++i >= k)
                    break;
            }
            return result;
        }
    }
    ```

-   [x] **Time Complexity :** O(n\*log n) where _n_ is the length of array

-   [x] **Space Complexity :** O(n) where _n_ is the length of array
