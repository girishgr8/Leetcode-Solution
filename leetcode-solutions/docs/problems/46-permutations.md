---
tags:
    - Array
    - Backtracking
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/permutations/](https://leetcode.com/problems/permutations/){:target="\_blank"}

**Approach : Backtracking :smile:**

=== "Java"

    ```java
    class Solution {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        public List<List<Integer>> permute(int[] nums) {
            solve(nums, new ArrayList<Integer>());
            return result;
        }

        public void solve(int nums[], List<Integer> list){
            if(list.size() == nums.length)
                result.add(new ArrayList<Integer>(list));

            for(int i = 0; i < nums.length; i++){
                if(list.contains(nums[i])) continue;
                list.add(nums[i]);
                solve(nums, list);
                list.remove(Integer.valueOf(nums[i]));
            }
        }
    }
    ```

-   [x] **Time Complexity :** O(2^n^\*k) where k = average length of combinations

-   [x] **Space Complexity :**
