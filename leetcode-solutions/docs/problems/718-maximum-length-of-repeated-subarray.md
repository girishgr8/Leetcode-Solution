---
tags:
    - Array
    - Binary Search
    - Dynamic Programming
    - Sliding Window
    - Rolling Hash
    - Hash Function
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/maximum-length-of-repeated-subarray/](https://leetcode.com/problems/maximum-length-of-repeated-subarray/){:target="\_blank"}

**Approach 1 : Brute Force - Recursion :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        public int findLength(int[] A, int[] B) {
            return solve(A, B, A.length, B.length, 0);
        }

        public int solve(int[] A, int[] B, int m, int n, int len){
            if(m <= 0 || n <= 0)
                return len;

            int c1 = len;
            if(A[m-1] == B[n-1])
                c1 = solve(A, B, m-1, n-1, len+1);

            int c2 = solve(A, B, m, n-1, 0);
            int c3 = solve(A, B, m-1, n, 0);
            return Math.max(c1, Math.max(c2, c3));
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(2^(m\*n)^) where m & n are lengths of arrays `A` and `B`

-   [x] **Space Complexity :** O(max(m,n)) where m & n are lengths of arrays `A` and `B`

<hr>

**Approach 2 : Dynamic Programming - Tabulation :smile:**

=== "Java"

    ```java
    class Solution {
        public int findLength(int[] A, int[] B) {
            int m = A.length, n = B.length;
            int[][] dp = new int[m + 1][n + 1];
            int max = 0;

            for(int i = 1; i <= m; i++){
                for(int j = 1; j <= n; j++){
                    if(A[i-1] == B[j-1]){
                        dp[i][j] = 1 + dp[i-1][j-1];
                        max = Math.max(max, dp[i][j]);
                    }
                }
            }
            return max;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(m\*n) where m & n are lengths of arrays `A` and `B`

-   [x] **Space Complexity :** O(m\*n) where m & n are lengths of arrays `A` and `B`
