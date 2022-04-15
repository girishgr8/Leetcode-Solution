---
tags:
    - Array
    - Matrix
    - Simulation
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/queens-that-can-attack-the-king/](https://leetcode.com/problems/queens-that-can-attack-the-king/){:target="\_blank"}

**Approach : Matrix Exploration + Simulation :smile:**

=== "Java"

    ```java
    class Solution {
        public List<List<Integer>> queensAttacktheKing(int[][] queens, int[] king) {
            List<List<Integer>> result = new ArrayList<List<Integer>>();
            boolean[][] board = new boolean[8][8];
            for(int i = 0; i < queens.length; i++)
                board[queens[i][0]][queens[i][1]] = true;

            int[] dir = {1, 0, -1};

            for(int dx : dir){
                for(int dy : dir){
                    if(dx == 0 && dy == 0)
                        continue;
                    int x = king[0];
                    int y = king[1];
                    while(x+dx >= 0 && x+dx < 8 && y+dy >= 0 && y+dy < 8){
                        x += dx;
                        y += dy;
                        if(board[x][y]){
                            result.add(Arrays.asList(x,y));
                            break;
                        }
                    }
                }
            }
            return result;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(1) i.e. O(8\*8) as it is a 8\*8 chessboard

-   [x] **Space Complexity :** O(1) i.e. O(8\*8) as it is a 8\*8 chessboard
