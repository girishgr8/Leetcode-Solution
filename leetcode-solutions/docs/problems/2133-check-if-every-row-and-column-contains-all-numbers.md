---
tags:
    - Array
    - Hash Table
    - Matrix
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/check-if-every-row-and-column-contains-all-numbers/](https://leetcode.com/problems/check-if-every-row-and-column-contains-all-numbers/){:target="\_blank"}

**Approach : HashTable Approach :smile:**

=== "Java"

    ```java
    class Solution {
        public boolean checkValid(int[][] matrix) {
            int n = matrix.length;
            int[] arr = new int[n + 1];

            for(int i = 0; i < n; i++){
                for(int j = 0; j < n; j++){
                    int num = matrix[i][j];
                    if(arr[num] == 1 || arr[num] > n)
                        return false;
                    arr[num] = 1;
                }
                Arrays.fill(arr, 0);
            }

            for(int i = 0; i < n; i++){
                for(int j = 0; j < n; j++){
                    int num = matrix[j][i];
                    if(arr[num] == 1 || arr[num] > n)
                        return false;
                    arr[num] = 1;
                }
                Arrays.fill(arr, 0);
            }

            return true;
        }
    }
    ```

=== "C++"

    ```c++
    ```

-   [x] **Time Complexity :** O(n^2^) where dimension of matrix is `n x n`

-   [x] **Space Complexity :** O(n) where dimension of matrix is `n x n`
