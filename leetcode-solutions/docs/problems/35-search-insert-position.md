---
tags:
    - Array
    - Binary Search
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/search-insert-position/](https://leetcode.com/problems/search-insert-position/){:target="\_blank"}

**Approach : Modified Binary Search :smile:**

=== "Java"

    ```java
    class Solution {
        public int searchInsert(int[] nums, int target) {
            int low = 0, high = nums.length - 1;
            while(low <= high){
                int mid = low + (high-low)/2;
                if(nums[mid] == target)
                    return mid;
                if(nums[mid] < target)
                    low = mid + 1;
                else
                    high = mid - 1;
            }
            return low;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(log n) where n = number of elements in array

-   [x] **Space Complexity :** O(1)
