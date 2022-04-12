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
    class Element{
        int freq, element;
        public Element(int element, int freq) {
            this.element = element;
            this.freq = freq;
        }
    }
    class Solution {
        public int[] topKFrequent(int[] nums, int k) {
            // O(1) time if k == nums.length
            if(k == nums.length)
                return nums;

            // create a map to store elements and their frequencies
            HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();

            // Minheap to store the top 'k' frequent elements
            PriorityQueue<Element> heap = new PriorityQueue<Element>((e1, e2) -> e1.freq - e2.freq);

            for(int i = 0; i < nums.length; i++)
                map.put(nums[i], map.getOrDefault(nums[i],0)+1);

            // add the unique elements of HashMap to Minheap
            for(Integer i: map.keySet()){
                heap.add(new Element(i,map.get(i)));
                // if size of heap becomes > k, extract the min element
                if(heap.size() > k)
                    heap.poll();
            }

            // Now our min heap contains top 'k' frequent elements
            int top[] = new int[k];
            int i = 0;

            // Return the top 'k' frequent elements present in the heap
            while(k-- > 0)
                top[i++] = heap.poll().element;

            return top;
        }
    }
    ```

-   [x] **Time Complexity :** O(n\*log k) where _n_ is the length of array

-   [x] **Space Complexity :** O(n) where _n_ is the length of array

<hr>

**Approach 2 : HashMap + Sorting**

=== "Java"

    ```java
    class Solution {
        public int[] topKFrequent(int[] nums, int k) {
            int[] result = new int[k];
            HashMap<Integer,Integer> map = new HashMap<Integer,Integer>();

            // Hashmap which stores (element, frequency)
            for(int i = 0; i < nums.length; i++)
                map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);

            // Create a list from the map
            List<Map.Entry<Integer, Integer>> list =
                new LinkedList<Map.Entry<Integer, Integer>>(map.entrySet());

            // Sort the list using lambda expression
            Collections.sort(list, (e1,e2) -> e2.getValue().compareTo(e1.getValue()));

            // put elements from sorted list to the result array
            int i = 0;
            for (Map.Entry<Integer, Integer> itr : list) {
                result[i++] = itr.getKey();
                if(i >= k)
                    break;
            }
            return result;
        }
    }
    ```

-   [x] **Time Complexity :** O(n\*log n) where _n_ is the length of array

-   [x] **Space Complexity :** O(n) where _n_ is the length of array
