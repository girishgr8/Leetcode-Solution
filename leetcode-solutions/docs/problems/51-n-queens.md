---
tags:
    - Array
    - Backtracking
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/n-queens/](https://leetcode.com/problems/n-queens/){:target="\_blank"}

**Approach : Recursion + Backtracking :smile:**

=== "Java"

    ```java
    class Solution {
        List<List<String>> result = new ArrayList<List<String>>();
        public List<List<String>> solveNQueens(int n) {
            char[][] board = new char[n][n];
            for(int i = 0; i < board.length; i++)
                Arrays.fill(board[i], '.');
            place(board, 0);
            return result;
        }

        public void place(char board[][], int row){
            if(row == board.length){
                List<String> list = new ArrayList<String>();
                for(int i = 0; i < board.length; i++)
                    list.add(String.valueOf(board[i]));
                result.add(list);
                return;
            }
            for(int col = 0; col < board.length; col++){
                if(isSafe(board, row, col)){
                    board[row][col] = 'Q';
                    place(board, row + 1);
                    board[row][col] = '.';
                }
            }
        }

        public boolean isSafe(char[][] board, int row, int col){
            if(!columnSafe(board, row, col) || !diagonalSafe(board, row, col))
                return false;
            return true;
        }

        public boolean columnSafe(char[][] board, int row, int col){
            for(int i = 0; i < board.length; i++){
                if(board[i][col] == 'Q')
                    return false;
            }
            return true;
        }

        public boolean diagonalSafe(char[][] board, int row, int col){
            // Primary diagonal
            for (int i = row - 1, j = col + 1; i >= 0 && j < board.length; i--, j++)
                if (board[i][j] == 'Q')
                    return false;
            // Secondary diagonal
            for (int i = row - 1, j = col - 1; i >= 0 && j >= 0; i--, j--)
                if (board[i][j] == 'Q')
                    return false;
            return true;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(N!) where _N_ is the number of queens

-   [x] **Space Complexity :** O(N) where _N_ is the number of queens
