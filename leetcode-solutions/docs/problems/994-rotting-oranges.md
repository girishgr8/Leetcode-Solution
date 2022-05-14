---
tags:
    - Array
    - Breadth-First Search
    - Matrix
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/rotting-oranges/](https://leetcode.com/problems/rotting-oranges/){:target="\_blank"}

**Approach : Multi-Source Breadth-First Search :smile:**

=== "Java"

    ```java
    class Pair{
        int rotTime;
        int[] position;
        public Pair(int rotTime, int[] position){
            this.rotTime = rotTime;
            this.position = position;
        }
    }

    class Solution {
        public int orangesRotting(int[][] grid) {
            Queue<Pair> queue = new LinkedList<Pair>();
            int oranges = 0;
            int m = grid.length, n = grid[0].length;
            boolean[][] visited = new boolean[m][n];

            for(int i = 0; i < m; i++){
                for(int j = 0; j < n; j++){
                    if(grid[i][j] > 0)
                        oranges++;
                    if(grid[i][j] == 2){
                        // these cells of rotten oranges are the multiple sources for BFS traversal
                        visited[i][j] = true;
                        queue.add(new Pair(0, new int[]{i, j}));
                    }
                }
            }

            int[][] dir = {{-1, 0}, {1, 0}, {0, 1}, {0, -1}};
            int time = -1;

            while(!queue.isEmpty()){
                Pair p = queue.poll();
                int i = p.position[0], j = p.position[1];
                int rotTime = p.rotTime;
                time = Math.max(time, rotTime);
                oranges--;
                for(int k = 0; k < dir.length; k++){
                    int x = i + dir[k][0];
                    int y = j + dir[k][1];
                    if(x >= m || x < 0 || y >= n || y < 0 || grid[x][y] == 0)
                        continue;
                    if(!visited[x][y]){
                        // visit cells having fresh oranges adjacent to cell of current rotten orange
                        visited[x][y] = true;
                        queue.add(new Pair(rotTime + 1, new int[]{x, y}));
                    }
                }
            }

            // if we visit all oranges, then return time
            if(oranges == 0)
                return Math.max(0, time);
            return -1;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(m\*n) where grid size is `m x n`

-   [x] **Space Complexity :** O(m\*n) where grid size is `m x n`
