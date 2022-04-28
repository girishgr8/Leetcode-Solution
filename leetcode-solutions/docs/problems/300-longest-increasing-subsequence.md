---
tags:
    - Array
    - Binary Search
    - Dynamic Programming
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/longest-increasing-subsequence/](https://leetcode.com/problems/longest-increasing-subsequence/){:target="\_blank"}

**Approach : Dynamic Programming - Tabulation :smile:**

=== "Java"

    ```java
    class Solution {
        public int lengthOfLIS(int[] nums) {
            int n = nums.length;
            int[] dp = new int[n];
            Arrays.fill(dp, 1);
            int max = 1;
            for(int i = 1; i < n; i++){
                for(int j = 0; j < i; j++){
                    if(nums[j] < nums[i] && dp[i] <= dp[j])
                        dp[i] = 1 + dp[j];                
                }
                max = Math.max(max, dp[i]);
            }  
            return max;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n^2^) where n = length of array `nums`

-   [x] **Space Complexity :** O(n) where n = length of array `nums`
