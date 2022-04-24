---
tags:
    - String
    - Dynamic Programming
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/shortest-common-supersequence/](https://leetcode.com/problems/shortest-common-supersequence/){:target="\_blank"}

**Approach : Dynamic Programming - Tabulation :smile:**

=== "Java"

    ```java
    class Solution {
        public String shortestCommonSupersequence(String str1, String str2) {
            int m = str1.length(), n = str2.length();
            int[][] dp = new int[m + 1][n + 1];

            for(int i = 1; i <= m; i++){
                for(int j = 1; j <= n; j++){
                    if(str1.charAt(i-1) == str2.charAt(j-1))
                        dp[i][j] = 1 + dp[i-1][j-1];
                    else
                        dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
                }
            }

            int lenLCS = dp[m][n];
            int size = m + n - lenLCS;
            char[] scs = new char[size];
            int i = m, j = n;
            while(i > 0 && j > 0){
                if(dp[i-1][j] == dp[i][j])
                    scs[--size] = str1.charAt(--i);
                else if(dp[i][j-1] == dp[i][j])
                    scs[--size] = str2.charAt(--j);
                else{
                    scs[--size] = str1.charAt(i-1);
                    i--;
                    j--;
                }
            }
            while(i > 0)
                scs[--size] = str1.charAt(--i);
            while(j > 0)
                scs[--size] = str2.charAt(--j);
            return String.valueOf(scs);
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(m\*n) where m & n are length of strings str1 and str2

-   [x] **Space Complexity :** O(m\*n) where m & n are length of strings str1 and str2
