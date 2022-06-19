---
tags:
    - Array
    - Two Pointers
    - Sorting
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/sort-colors/](https://leetcode.com/problems/sort-colors/){:target="\_blank"}

**Approach 1 : Counting Sort approach :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        public void sortColors(int[] nums) {
            int[] arr = new int[3];
            int i = 0;

            for(int color: nums)  arr[color]++;

            for(int color = 0; color < 3; color++){
                while(arr[color]-- > 0)
                    nums[i++] = color;
            }
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = size of array

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : Dutch National Flag Sort(DNF Sort) approach :smile:**

The algorithm is as follows:

1. Initialise `low` = 0, `mid` = 0 and `high` = n - 1
2. `[0,low]` indicates region of 0's in array
3. `[low, mid-1]` indicates region of 1's in array
4. `[mid, high-1]` indicates unknown region in array
5. `[high, n-1]` indicates region of 2's in array
6. Now, perform following steps while `mid <= high` & check `arr[mid]` value:

    a. If `0`, then swap `arr[low]` and `arr[mid]` and do `low++`, `mid++`

    b. If `1`, then `mid++`

    c. If `2`, then swap `arr[mid]` and `arr[high]` and do `high--`

=== "Java"

    ```java
    class Solution {
        public void sortColors(int[] nums) {
            int n = nums.length;
            int low = 0, mid = 0, high = n - 1;

            while(mid <= high){
                if(nums[mid] == 0){
                    int temp = nums[low];
                    nums[low] = nums[mid];
                    nums[mid] = temp;
                    low++;
                    mid++;
                }
                else if(nums[mid] == 1){
                    mid++;
                }
                else{
                    int temp = nums[mid];
                    nums[mid] = nums[high];
                    nums[high] = temp;
                    high--;
                }
            }
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where n = size of array

-   [x] **Space Complexity :** O(1)
