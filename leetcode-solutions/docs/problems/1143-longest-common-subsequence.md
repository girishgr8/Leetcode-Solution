---
tags:
    - String
    - Dynamic Programming
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/longest-common-subsequence/](https://leetcode.com/problems/longest-common-subsequence/){:target="\_blank"}

**Approach : Dynamic Programming - Tabulation :smile:**

=== "Java"

    ```java
    class Solution {
        public int longestCommonSubsequence(String text1, String text2) {
            int m = text1.length(), n = text2.length();
            int[][] dp = new int[m + 1][n + 1];

            for(int i = 1; i <= m; i++){
                for(int j = 1; j <= n; j++){
                    if(text1.charAt(i-1) == text2.charAt(j-1))
                        dp[i][j] = 1 + dp[i-1][j-1];
                    else
                        dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
                }
            }
            return dp[m][n];
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(m\*n) where m & n are length of strings text1 and text2

-   [x] **Space Complexity :** O(m\*n) where m & n are length of strings text1 and text2
