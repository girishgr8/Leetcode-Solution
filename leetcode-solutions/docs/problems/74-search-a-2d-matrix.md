---
tags:
    - Array
    - Binary Search
    - Matrix
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/search-a-2d-matrix/](https://leetcode.com/problems/search-a-2d-matrix/){:target="\_blank"}

**Approach : Binary Search :smile:**

=== "Java"

    ```java
    class Solution {
        public boolean searchMatrix(int[][] matrix, int target) {
            int m = matrix.length, n = matrix[0].length;
            int top = 0, bottom = m - 1;
            int left = 0, right = n - 1;
            int row = 0;
            while(top <= bottom){
                int mid = top + (bottom - top)/2;
                if(matrix[mid][left] <= target && matrix[mid][right] >= target){
                    row = mid;
                    break;
                }
                if(matrix[mid][left] > target)
                    bottom = mid - 1;
                else if(matrix[mid][right] < target)
                    top = mid + 1;
            }
            while(left <= right){
                int mid = left + (right - left)/2;
                if(matrix[row][mid] == target)
                    return true;
                if(matrix[row][mid] < target)
                    left = mid + 1;
                else
                    right =  mid - 1;
            }
            return false;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(log m\*n) where m = numeber of rows, n = number of columns

-   [x] **Space Complexity :** O(1)
