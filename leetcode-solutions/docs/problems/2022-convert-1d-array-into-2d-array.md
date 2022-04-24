---
tags:
    - Array
    - Matrix
    - Simulation
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/convert-1d-array-into-2d-array/](https://leetcode.com/problems/convert-1d-array-into-2d-array/){:target="\_blank"}

**Approach : Simulation :smile:**

-   To convert 1-D array to 2-D array, we can use formula `mat[i][j]=mat[c*i+j]`, where c is the number of columns.

=== "Java"

    ```java
    class Solution {
        public int[][] construct2DArray(int[] original, int m, int n) {
            int size = original.length;
            if(size != m * n)
                return new int[][]{};

            int[][] mat = new int[m][n];

            for(int i = 0; i < original.length; i++)
                mat[i/n][i % n] = original[i];

            return mat;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(m\*n) where size of new matrix is m\*n

-   [x] **Space Complexity :** O(m\*n) where size of new matrix is m\*n
