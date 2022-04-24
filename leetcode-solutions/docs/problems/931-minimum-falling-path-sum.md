---
tags:
    - Array
    - Dynamic Programming
    - Matrix
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/minimum-falling-path-sum/](https://leetcode.com/problems/minimum-falling-path-sum/){:target="\_blank"}

**Approach 1 : Brute Force (Time Limit Exceeded) :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        public int minFallingPathSum(int[][] matrix) {
            int min = Integer.MAX_VALUE;
            for(int i = 0; i < matrix.length; i++)
                min = Math.min(min, solve(matrix, 0, i, 0));
            return min;
        }
        public int solve(int[][] matrix, int r, int c, int sum){
            int n = matrix.length;
            if(r < 0 || r >= n)
                return sum;
            if(c < 0 || c >= n){
                if(r != n)
                    return Integer.MAX_VALUE;
                return sum;
            }
            sum += matrix[r][c];
            int below = solve(matrix, r + 1, c, sum);
            int diagLeft = solve(matrix, r + 1, c - 1, sum);
            int diagRight = solve(matrix, r + 1, c + 1, sum);

            return Math.min(below, Math.min(diagLeft, diagRight));
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :**

-   [x] **Space Complexity :**

<hr>

**Approach 2 : Dynamic Programming - Tabulation :smile:**

=== "Java"

    ```java
    class Solution {
        public int minFallingPathSum(int[][] matrix) {
            int n = matrix.length;
            int[][] dp = new int[n][n];
            for(int i = 0; i < n; i++)
                dp[n-1][i] = matrix[n-1][i];

            for(int i = n - 2; i >= 0; i--){
                for(int j = 0; j < n; j++){
                    if(j == 0)
                        dp[i][j] = Math.min(dp[i+1][j], dp[i+1][j+1]);
                    else if(j == n - 1)
                        dp[i][j] = Math.min(dp[i+1][j], dp[i+1][j-1]);
                    else
                        dp[i][j] = Math.min(dp[i+1][j], Math.min(dp[i+1][j-1], dp[i+1][j+1]));
                    dp[i][j] += matrix[i][j];
                }
            }
            int min = dp[0][0];
            for(int i = 1; i < n; i++)
                min = Math.min(min, dp[0][i]);
            return min;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n^2^) where size of matrix is n \* n

-   [x] **Space Complexity :** O(n^2^) where size of matrix is n \* n
