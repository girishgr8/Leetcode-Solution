---
tags:
    - Array
    - Hash Table
    - Matrix
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/set-matrix-zeroes/](https://leetcode.com/problems/set-matrix-zeroes/){:target="\_blank"}

=== "Java"

    ```java
    class Solution {
        public void setZeroes(int[][] matrix) {
            Set<Integer> rows = new HashSet<Integer>();
            Set<Integer> cols = new HashSet<Integer>();
            for(int i = 0; i < matrix.length; i++){
                for(int j = 0; j < matrix[i].length; j++){
                    if(matrix[i][j] == 0){
                        rows.add(i);
                        cols.add(j);
                    }
                }
            }
            for(int i = 0; i < matrix.length; i++){
                for(int j = 0; j < matrix[i].length; j++){
                    if(rows.contains(i) || cols.contains(j)){
                        matrix[i][j] = 0;
                    }
                }
            }
        }
    }
    ```

-   [x] **Time Complexity :** O(m\*n) where (_m,n_) is the dimension of matrix

-   [x] **Space Complexity :** O(m\*n) where (_m,n_) is the dimension of matrix
