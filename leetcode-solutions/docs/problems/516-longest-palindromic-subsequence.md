---
tags:
    - String
    - Dynamic Programming
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/longest-palindromic-subsequence/](https://leetcode.com/problems/longest-palindromic-subsequence/){:target="\_blank"}

**Approach : Dynamic Programming - Tabulation :smile:**

=== "Java"

    ```java
    class Solution {
        public int longestPalindromeSubseq(String s) {
            String t = new StringBuilder(s).reverse().toString();
            int n = s.length();
            int[][] dp = new int[n + 1][n + 1];

            for(int i = 1; i <= n; i++){
                for(int j = 1; j <= n; j++){
                    if(s.charAt(i-1) == t.charAt(j-1))
                        dp[i][j] = 1 + dp[i-1][j-1];
                    else
                        dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
                }
            }
            return dp[n][n];
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n^2^) where n = length of string `s`

-   [x] **Space Complexity :** O(n^2^) where n = length of string `s`
