---
tags:
    - Two Pointers
    - String
    - Dynamic Programming
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/is-subsequence/](https://leetcode.com/problems/is-subsequence/){:target="\_blank"}

**Approach 1 : LCS approach using Dynamic Programming - Tabulation :sweat_smile:**

-   If string `s` has to be subsequence of string `t`, then length of `LCS(s, t)` = length of string `s`

=== "Java"

    ```java
    class Solution {
        public boolean isSubsequence(String s, String t) {
            int m = s.length(), n = t.length();
            int[][] dp = new int[m + 1][n + 1];

            for(int i = 1; i <= m; i++){
                for(int j = 1; j <= n; j++){
                    if(s.charAt(i-1) == t.charAt(j-1))
                        dp[i][j] = 1 + dp[i-1][j-1];
                    else
                        dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
                }
            }
            return (m == dp[m][n]);
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(m\*n) where m & n are length of strings `s` and `t`

-   [x] **Space Complexity :** O(m\*n) where m & n are length of strings `s` and `t`

<hr>

**Approach 2 : Two Pointer approach :smile:**

-   The idea is to use two pointers, first pointing at string `s` and second pointing at string `t`.
-   Whenever the characters match pointed by these pointers, increment pointer pointing at strings `s` and `t` both.
-   Otherwise increment pointer pointing at string `t`.

=== "Java"

    ```java
    class Solution {
        public boolean isSubsequence(String s, String t) {
            int m = s.length(), n = t.length();
            int i = 0, j = 0;

            while(i < m && j < n){
                if(s.charAt(i) == t.charAt(j))
                    i++;
                j++;
            }
            return (i == m);
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(max(m,n)) where m & n are length of strings `s` and `t`

-   [x] **Space Complexity :** O(1)
