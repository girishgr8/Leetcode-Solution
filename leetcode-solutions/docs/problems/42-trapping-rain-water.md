---
tags:
    - Array
    - Two Pointers
    - Dynamic Programming
    - Stack
    - Monotonic Stack
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/trapping-rain-water/](https://leetcode.com/problems/trapping-rain-water/){:target="\_blank"}

**Approach : Prefix Array approach :smile:**

=== "Java"

    ```java
    class Solution {
        public int trap(int[] height) {
            int n = height.length;
            int[] left = new int[n];
            int[] right = new int[n];
            left[0] = height[0];
            right[n-1] = height[n-1];

            for(int i = 1; i < n; i++){
                left[i] = Math.max(left[i-1], height[i]);
                right[n-1-i] = Math.max(right[n-i], height[n-1-i]);
            }
            int total = 0;
            for(int i = 0; i < n; i++)
                total += Math.min(left[i], right[i]) - height[i];
            return total;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where _n_ is the number of bars

-   [x] **Space Complexity :** O(n) where _n_ is the number of bars
