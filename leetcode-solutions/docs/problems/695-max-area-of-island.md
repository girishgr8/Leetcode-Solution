---
tags:
    - Array
    - Depth-First Search
    - Breadth-First Search
    - Union Find
    - Matrix
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/max-area-of-island/](https://leetcode.com/problems/max-area-of-island/){:target="\_blank"}

**Approach : DFS :smile:**

=== "Java"

    ```java
    class Solution {
        boolean[][] visited;
        public int maxAreaOfIsland(int[][] grid) {
            int m = grid.length, n = grid[0].length;
            visited = new boolean[m][n];
            int largestArea = 0;
            for(int i = 0; i < m; i++){
                for(int j = 0; j < n; j++){
                    if(grid[i][j] == 1 && !visited[i][j])
                        largestArea = Math.max(largestArea, explore(grid, m, n, i, j));
                }
            }
            return largestArea;
        }
        public int explore(int[][] grid, int m, int n, int row, int col){
            // base case 1: if we go out of bounds of the matrix
            if(row < 0 || col < 0 || row >= m || col >= n)
                return 0;
            // base case 2: if we are not currently at island (grid[i][j] == 0)
            //              or we have already visited this island
            if(grid[row][col] == 0 || visited[row][col])
                return 0;
            // visit the current island
            visited[row][col] = true;
            // recursively visit islands to left, right, above below
            int left = explore(grid, m, n, row, col-1);
            int right = explore(grid, m, n, row, col+1);
            int above = explore(grid, m, n, row-1, col);
            int below = explore(grid, m, n, row+1, col);
            // maximum area would be 1 + sum of area of its neighbouring islands
            // we add 1 because we should also add current island's area
            int maxArea = 1 + left + right + above + below;
            return maxArea;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(m\*n) where m = numeber of rows, n = number of columns

-   [x] **Space Complexity :** O(m\*n) where m = numeber of rows, n = number of columns
