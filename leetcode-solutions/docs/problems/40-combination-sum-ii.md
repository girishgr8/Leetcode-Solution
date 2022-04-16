---
tags:
    - Array
    - Backtracking
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/combination-sum-ii/](https://leetcode.com/problems/combination-sum-ii/){:target="\_blank"}

**Approach : Backtracking :smile:**

=== "Java"

    ```java
    class Solution {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        public List<List<Integer>> combinationSum2(int[] candidates, int target) {
            Arrays.sort(candidates);
            solve(candidates, target, 0, new ArrayList<Integer>());
            return result;
        }

        public void solve(int[] candidates, int target, int curr, List<Integer> list){
            int n = candidates.length;
            if(target == 0){
                result.add(new ArrayList(list));
                return;
            }
            if(curr >= n || target < 0)
                return;

            for(int i = curr; i < n; i++){
                if(i > curr && candidates[i] == candidates[i-1]) continue;
                list.add(candidates[i]);
                solve(candidates, target-candidates[i], i + 1, list);
                list.remove(new Integer(candidates[i]));
            }
        }
    }
    ```

-   [x] **Time Complexity :** O(2^n^\*k) where k = average length of combinations

-   [x] **Space Complexity :**
