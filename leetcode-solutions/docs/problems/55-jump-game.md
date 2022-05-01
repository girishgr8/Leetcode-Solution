---
tags:
    - Array
    - Dynamic Programming
    - Greedy
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/jump-game/](https://leetcode.com/problems/jump-game/){:target="\_blank"}

**Approach : Greedy :smile:**

=== "Java"

    ```java
    class Solution{
        public boolean canJump(int[] nums){
            int n = nums.length;
            int lastIndex = n - 1;
            for (int i = n - 1; i >= 0; i--){
                if (nums[i] + i >= lastIndex){
                    lastIndex = i;
                }
            }
            return (lastIndex == 0);
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n is length of array `nums`

-   [x] **Space Complexity :** O(1)
