---
tags:
    - Array
    - Dynamic Programming
    - Greedy
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/jump-game-ii/](https://leetcode.com/problems/jump-game-ii/){:target="\_blank"}

**Approach : Dynamic Programming -Tabulation :smile:**

=== "Java"

    ```java
    class Solution {
        public int jump(int[] nums) {
            int n = nums.length;
            int[] dp = new int[n];
            Arrays.fill(dp, Integer.MAX_VALUE);
            dp[0] = 0;
            for(int i = 0; i < n; i++){
                int reach = Math.min(n - 1, i + nums[i]);
                for(int j = i + 1; j <= reach; j++){
                    dp[j] = Math.min(dp[j], 1 + dp[i]);
                }
            }
            return dp[n-1];
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n^2^) where n is length of array `nums`

-   [x] **Space Complexity :** O(n) where n is length of array `nums`
