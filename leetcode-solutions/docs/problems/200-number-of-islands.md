---
tags:
    - Array
    - Depth-First Search
    - Breadth-First Search
    - Union Find
    - Matrix
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/number-of-islands/](https://leetcode.com/problems/number-of-islands/){:target="\_blank"}

**Approach : DFS :smile:**

=== "Java"

    ```java
    class Solution {
        boolean[][] visited;
        public int numIslands(char[][] grid) {
            int m = grid.length, n = grid[0].length;
            visited = new boolean[m][n];
            int islands = 0;
            for(int i = 0; i < m; i++){
                for(int j = 0; j < n; j++){
                    if(grid[i][j] == '1' && !visited[i][j])
                        islands += explore(grid, m, n, i, j);
                }
            }
            return islands;
        }

        public int explore(char[][] grid, int m, int n, int row, int col){
            // base case 1: if we go out of bounds of the matrix
            if(row < 0 || col < 0 || row >= m || col >= n)
                return 0;
            // base case 2: if we are not currently at island (grid[i][j] == '0')
            //              or we have already visited this island
            if(grid[row][col] == '0' || visited[row][col])
                return 0;
            // visit the current island
            visited[row][col] = true;
            // recursively visit islands to left, right, above below
            int left = explore(grid, m, n, row, col-1);
            int right = explore(grid, m, n, row, col+1);
            int above = explore(grid, m, n, row-1, col);
            int below = explore(grid, m, n, row+1, col);
            return 1;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(m\*n) where m = numeber of rows, n = number of columns

-   [x] **Space Complexity :** O(m\*n) where m = numeber of rows, n = number of columns
