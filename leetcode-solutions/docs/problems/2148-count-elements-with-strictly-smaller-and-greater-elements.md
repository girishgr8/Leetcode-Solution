---
tags:
    - Array
    - Sorting
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/count-elements-with-strictly-smaller-and-greater-elements/](https://leetcode.com/problems/count-elements-with-strictly-smaller-and-greater-elements/){:target="\_blank"}

**Approach : Linear Scan :smile:**

-   Iterate through array `nums` first time and keep find minimum and maximum element of the array
-   While iterating through array `nums` again check if element is larger than minimum element of array and smaller than maximum element of array

=== "Java"

    ```java
    class Solution {
        public int countElements(int[] nums) {
            int n = nums.length;
            int count = 0;
            int min = nums[0];
            int max = nums[0];

            for(int i = 1; i < n; i++){
                min = Math.min(nums[i], min);
                max = Math.max(nums[i], max);
            }

            for(int i = 0; i < n; i++){
                if(min < nums[i] && nums[i] < max)
                    count++;
            }
            return count;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = length of array `nums`

-   [x] **Space Complexity :** O(1)
