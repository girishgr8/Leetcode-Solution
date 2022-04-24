---
tags:
    - Array
    - Matrix
    - Simulation
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/reshape-the-matrix/](https://leetcode.com/problems/reshape-the-matrix/){:target="\_blank"}

**Approach : Simulation :smile:**

-   To convert 1-D array to 2-D array, we can use formula `mat[i][j]=mat[c*i+j]` , where c is the number of columns.

-   To convert 2-D array to 1-D array, we can use formula `mat[i/c][i%c]=mat[i]` , where c is the number of columns.

=== "Java"

    ```java
    class Solution {
        public int[][] matrixReshape(int[][] mat, int r, int c) {
            int m = mat.length, n = mat[0].length;
            if(m * n != r * c)
                return mat;

            int[][] newMat = new int[r][c];
            int[] temp = new int[m*n];

            for(int i = 0; i < m; i++)
                for(int j = 0; j < n; j++)
                    temp[n*i+j] = mat[i][j];

            for(int i = 0; i < temp.length; i++)
                newMat[i/c][i%c] = temp[i];

            return newMat;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(m\*n) where size of original matrix is m\*n

-   [x] **Space Complexity :** O(m\*n) where size of original matrix is m\*n
