---
tags:
    - Array
    - Hash Table
    - Sorting
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/longest-harmonious-subsequence/](https://leetcode.com/problems/longest-harmonious-subsequence/){:target="\_blank"}

**Approach : HashMap :smile:**

=== "Java"

    ```java
    class Solution {
        public int findLHS(int[] nums) {
            int lhs = 0;
            Map<Integer, Integer> map = new HashMap<Integer, Integer>();

            for(int i = 0; i < nums.length; i++)
                map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);

            for(Integer key: map.keySet()){
                if(map.containsKey(key + 1))
                    lhs = Math.max(lhs, map.get(key) + map.get(key+1));
            }

            return lhs;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = length of array `nums`

-   [x] **Space Complexity :** O(n) where n = length of array `nums`
