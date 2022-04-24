---
tags:
    - Array
    - Dynamic Programming
    - Matrix
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/minimum-falling-path-sum-ii/](https://leetcode.com/problems/minimum-falling-path-sum-ii/){:target="\_blank"}

**Approach 1 : Brute Force (Time Limit Exceeded) :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        public int minFallingPathSum(int[][] grid) {
            int min = Integer.MAX_VALUE;
            for(int i = 0; i < grid.length; i++){
                min = Math.min(min, solve(grid, 0, i, 0));
            }
            return min;
        }

        public int solve(int[][] grid, int r, int c, int sum){
            int n = grid.length;
            if(r < 0 || r >= n)
                return sum;
            if((c < 0 || c >= n) && r != n)
                return Integer.MAX_VALUE;

            sum += grid[r][c];
            int left = Integer.MAX_VALUE, right = Integer.MAX_VALUE;
            for(int i = 0; i < c; i++)
                left = Math.min(left, solve(grid, r + 1, i, sum));
            for(int i = c + 1; i < n; i++)
                right = Math.min(right, solve(grid, r + 1, i, sum));

            int min = Math.min(left, right);
            return min != Integer.MAX_VALUE ? min : sum;
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
        public int minFallingPathSum(int[][] grid) {
            int n = grid.length;
            int[][] dp = new int[n][n];
            for(int i = 0; i < n; i++)
                dp[n-1][i] = grid[n-1][i];

            for(int i = n - 2; i >= 0; i--){
                for(int j = 0; j < n; j++){
                    int min = Integer.MAX_VALUE;
                    for(int k = 0; k < j; k++)
                        min = Math.min(min, dp[i + 1][k]);
                    for(int k = j + 1; k < n; k++)
                        min = Math.min(min, dp[i + 1][k]);
                    dp[i][j] += min + grid[i][j];
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
