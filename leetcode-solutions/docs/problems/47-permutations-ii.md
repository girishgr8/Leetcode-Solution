---
tags:
    - Array
    - Backtracking
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/permutations-ii/](https://leetcode.com/problems/permutations-ii/){:target="\_blank"}

**Approach : Depth-First Search + Backtracking Approach :smile:**

=== "Java"

    ```java
    class Solution {
        List<List<Integer>> result;
        public List<List<Integer>> permuteUnique(int[] nums) {

            Map<Integer,Integer> map = new HashMap<Integer,Integer>();
            result = new ArrayList<List<Integer>>();

            for(int i = 0; i < nums.length; i++)
                map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);

            permute(0, nums.length, map, new ArrayList<Integer>());
            return result;
        }

        public void permute(int i, int n, Map<Integer,Integer> map, List<Integer> list){
            if(i >= n){
                result.add(new ArrayList<Integer>(list));
                return;
            }

            for(Integer key : map.keySet()){
                if(map.get(key) == 0)
                    continue;
                list.add(key);
                map.put(key, map.get(key) - 1);
                permute(i + 1, n, map, list);
                list.remove(i);
                map.put(key, map.get(key) + 1);
            }
            return;
        }
    }
    ```

=== "C++"

    ```c++
    ```

-   [x] **Time Complexity :** O(n!) where n = length of array `nums`

-   [x] **Space Complexity :** O(n) where n = length of array `nums`
