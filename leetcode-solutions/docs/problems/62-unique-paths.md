---
tags:
    - Math
    - Dynamic Programming
    - Combinatorics
---

**Leetcode Problem Link :** [https://leetcode.com/problems/unique-paths/](https://leetcode.com/problems/unique-paths/){:target="\_blank"}

<img src="https://img.shields.io/badge/-Medium-3CB43C.svg" />
<img src="https://img.shields.io/badge/-Math-0069ff.svg" />
<img src="https://img.shields.io/badge/-Dynamic Programming-0069ff.svg" />
<img src="https://img.shields.io/badge/-Combinatorics-0069ff.svg" />

[Solution Video]()

<hr>

**Approach 1 : Brute Force :sweat_smile:**

Try all possible cases to reach to the final position.

=== "Java"

    ```java
    class Solution {
        public int uniquePaths(int m, int n) {
            // base case
            if(m == 1 || n == 1) return 1;

            // move down
            int downMove = uniquePaths(m-1, n);
            // move right
            int rightMove = uniquePaths(m, n-1);

            return downMove + rightMove;
        }
    }
    ```

-   [x] **Time Complexity :** O(2^mn^)

-   [x] **Space Complexity :** O(max(m,n))

<hr>

**Approach 2 : Memoization :slight_smile:**

Here, we store the value for number of unique paths calculated for cell(i, j), so that if we encounter same subproblem in further recursive calls, we can directly use the calculated value instead of re-calculating for that cell.

=== "Java"

    ```java
    class Solution {
        private Map<String, Integer> map = new HashMap<String, Integer>();
        public int uniquePaths(int m, int n) {
            // base case
            if(m == 1 || n == 1) return 1;

            // check if we have already calculated unique paths for cell(m, n)
            String cell = new String(m + "," + n);

            // if yes, then get its value from our memoization table
            if(map.containsKey(cell))
                return map.get(cell);

            // else, explore the down move
            int downMove = uniquePaths(m-1, n);
            // explore the right move
            int rightMove = uniquePaths(m, n-1);

            // put the value obtained for unique paths from cell(m, n)
            map.put(cell, downMove + rightMove);

            return downMove + rightMove;
        }
    }
    ```

-   [x] **Time Complexity :** O(2^mn^)

-   [x] **Space Complexity :** O(max(m,n))

<hr>

**Approach 3 : Dynamic Programming :smiley:**

Using DP, we find the number of unique paths from a given cell is equal to as the sum of the values of its previous possible states.
`dp[i,j] = dp[i-1,j] + dp[i,j-1]` gives us the idea. To reach the position `(i, j)`, the path should either be coming from `(i-1, j)` or `(i, j-1)`. Now, we can use either top-down or bottom-up approach to calculate the number of unique paths.

**Approach 3.1 : Top-Down Dynamic Programming**

We start from top-left corner i.e. `(0, 0)` and finding paths in forward approach by using the formula `dp[i][j] = dp[i-1][j] + dp[i][j-1]`. The base case here is when `i == 0 || j == 0`, `dp[i][j] = 1`. Here, `dp[i][j]` represents the number of paths from cell (0, 0) to cell (i, j).

=== "Java"

    ```java
    class Solution {
        public int uniquePaths(int m, int n) {
            int[][] dp = new int[m][n];

            for(int i = 0; i < m; i++){
                for(int j = 0; j < n ; j++){
                    if(i == 0 || j == 0)
                        dp[i][j] = 1;
                    else
                        dp[i][j] = dp[i][j-1] + dp[i-1][j];
                }
            }
            return dp[m-1][n-1];
        }
    }
    ```

-   [x] **Time Complexity :** O(m\*n)

-   [x] **Space Complexity :** O(m\*n)

**Approach 3.2: Bottom-Up Dynamic Programming**

We will start from the bottom-right corner (m, n) and find finding paths using backward approach using the formula `dp[i][j] = dp[i+1][j] + dp[i][j+1]`, where m = no. of rows and n = no. of columns. The base case here is when `i == m-1 || j == n-1`, `dp[i][j] = 1`. Here, `dp[i][j]` represents the number of paths from cell (m, n) to cell (i, j).

=== "Java"

    ```java
    class Solution {
        public int uniquePaths(int m, int n) {
            int[][] dp = new int[m][n];

            for(int i = m - 1; i >= 0; i--){
                for(int j = n - 1; j >= 0; j--){
                    if(i == m - 1 || j == n - 1)
                        dp[i][j] = 1;
                    else
                        dp[i][j] = dp[i][j+1] + dp[i+1][j];
                }
            }
            return dp[0][0];
        }
    }
    ```

-   [x] **Time Complexity :** O(m\*n)

-   [x] **Space Complexity :** O(m\*n)
