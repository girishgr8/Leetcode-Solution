---
tags:
    - Array
    - Binary Search
    - Matrix
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix/](https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix/){:target="\_blank"}

**Approach 1 : Brute Force Approach**

=== "Java"

    ```java
    class Solution {
        public int countNegatives(int[][] grid) {
            int count = 0;

            for(int i = 0; i < grid.length; i++){
                for(int j = 0; j < grid[i].length; j++){
                    if(grid[i][j] < 0)
                        count++;
                }
            }

            return count;
        }
    }
    ```

=== "C++"

    ```c++
    class Solution {
    public:
        int countNegatives(vector<vector<int>>& grid) {
            int count = 0;

            for(int i = 0; i < grid.size(); i++){
                for(int j = 0; j < grid[i].size(); j++){
                    if(grid[i][j] < 0)
                        count++;
                }
            }

            return count;
        }
    };
    ```

-   [x] **Time Complexity :** O(m\*n) where _(m,n)_ is the dimension of the grid

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : Binary Search (on each row)**

=== "Java"

    ```java
    class Solution {
        public int countNegatives(int[][] grid) {
            int count = 0;
            // m = no. of rows, n = no. of columns
            int m = grid.length, n = grid[0].length;

            for(int i = 0; i < grid.length; i++){
                int low = 0, high = n - 1;
                // Apply Binary Search on each row
                while(low <= high){
                    int mid = low + (high - low)/2;
                    // If the number at 'mid' is -ve,
                    // that means all the numbers to its right will also be -ve
                    // So count them and solve for left part
                    if(grid[i][mid] < 0){
                        count += high - mid + 1;
                        high = mid - 1;
                    }
                    // Otherwise, check if -ve number is present on right part
                    else{
                        low = mid + 1;
                    }
                }
            }
            return count;
        }
    }
    ```

=== "C++"

    ```c++
    class Solution {
    public:
        int countNegatives(int[][] grid) {
            int count = 0;
            int m = grid.length, n = grid[0].length;

            for(int i = 0; i < grid.length; i++){
                int low = 0, high = n - 1;
                while(low <= high){
                    int mid = low + (high - low)/2;
                    if(grid[i][mid] < 0){
                        count += high - mid + 1;
                        high = mid - 1;
                    }
                    else{
                        low = mid + 1;
                    }
                }
            }
            return count;
        }
    };
    ```

-   [x] **Time Complexity :** O(m\*log<sub>2</sub>n) where _m_ = number of rows & _n_ = number of columns

-   [x] **Space Complexity :** O(1)
