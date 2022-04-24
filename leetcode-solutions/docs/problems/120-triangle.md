---
tags:
    - Array
    - Dynamic Programming
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/triangle/](https://leetcode.com/problems/triangle/){:target="\_blank"}

**Approach : Dynamic Programming - Tabulation :smile:**

=== "Java"

    ```java
    class Solution {
        public int minimumTotal(List<List<Integer>> triangle) {
            int n = triangle.size();
            int[][] dp = new int[n][n];
            List<Integer> list = triangle.get(n-1);
            for(int c = 0; c < n; c++)
                dp[n-1][c] = list.get(c);

            for(int i = n-2; i >= 0; i--){
                list = triangle.get(i);
                for(int j = 0; j <= i; j++){
                    dp[i][j] = list.get(j) + Math.min(dp[i+1][j], dp[i+1][j+1]);
                }
            }
            return dp[0][0];
        }
    }
    ```

-   [x] **Time Complexity :** O(m\*n) where m & n are dimensions of triangle

-   [x] **Space Complexity :** O(m\*n) where m & n are dimensions of triangle
