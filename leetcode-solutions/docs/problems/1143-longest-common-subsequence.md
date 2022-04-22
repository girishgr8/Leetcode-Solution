---
tags:
    - String
    - Dynamic Programming
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/longest-common-subsequence/](https://leetcode.com/problems/longest-common-subsequence/){:target="\_blank"}

**Approach 1 : Brute Force - Recursion :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        public int longestCommonSubsequence(String text1, String text2) {
            return LCS(text1, text2, text1.length(), text2.length());
        }
        public int LCS(String s1, String s2, int i, int j){
            if(i == 0 || j == 0)
                return 0;
            if(s1.charAt(i-1) == s2.charAt(j-1))
                return 1 + LCS(s1, s2, i-1, j-1);
            else
                return Math.max(LCS(s1, s2, i-1, j), LCS(s1, s2, i, j-1));
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(2^(m\*n)) where m & n are length of strings text1 and text2

-   [x] **Space Complexity :** O(max(m,n)) where m & n are length of strings text1 and text2

<hr>

**Approach 2 : Dynamic Programming - Memoization :smile:**

=== "Java"

    ```java
    class Solution {
        int[][] dp;
        public int longestCommonSubsequence(String text1, String text2) {
            int m = text1.length(), n = text2.length();
            dp = new int[m + 1][n + 1];
            return LCS(text1, text2, m, n);
        }
        public int LCS(String s1, String s2, int i, int j){
            if(i == 0 || j == 0)
                return 0;

            if(dp[i][j] != 0)
                return dp[i][j];

            if(s1.charAt(i-1) == s2.charAt(j-1))
                dp[i][j] = 1 + LCS(s1, s2, i-1, j-1);
            else
                dp[i][j] = Math.max(LCS(s1, s2, i-1, j), LCS(s1, s2, i, j-1));
            return dp[i][j];
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(m\*n) where m & n are length of strings text1 and text2

-   [x] **Space Complexity :** O(m\*n) where m & n are length of strings text1 and text2

<hr>

**Approach 3 : Dynamic Programming - Tabulation :smile:**

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
