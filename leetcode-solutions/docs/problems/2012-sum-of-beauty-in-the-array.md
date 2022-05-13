---
tags:
    - Array
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/sum-of-beauty-in-the-array/](https://leetcode.com/problems/sum-of-beauty-in-the-array/){:target="\_blank"}

-   For the beauty value of the `i`^`th`^ element to be 2, it should be greater than all the elements on its left and smaller than all the elements on its right.
-   So, it should be greater than the maximum of all elements on the left and smaller than minimum of all elements on the right.

**Approach : Prefix & Suffix arrays for precomputation :smile:**

-   Idea is pre-compute maximum element to its left and minimum element to its right for each element the array `nums`.
-   We can use suffix & prefix arrays.
-   `prefix[i]` will store maximum values from `[0, i-1]`
-   `suffix[i]` will store minimum values from `[i+1, n-1]`

=== "Java"

    ```java
    class Solution {
        public int sumOfBeauties(int[] nums) {
            int n = nums.length;
            int[] maxToLeft = new int[n];
            int[] minToRight = new int[n];
            int[] beauty = new int[n];
            int beautySum = 0;

            maxToLeft[0] = nums[0];
            minToRight[n-1] = nums[n-1];

            for(int i = 1, j = n - i; i < n - 1; ++i, --j){
                if(nums[i-1] < nums[i] && nums[i] < nums[i+1])
                    beauty[i] = 1;
                maxToLeft[i] = Math.max(maxToLeft[i-1], nums[i-1]);
                minToRight[j-1] = Math.min(minToRight[j], nums[j]);
            }

            for(int i = 1; i < n - 1; ++i){
                if(maxToLeft[i] < nums[i] && nums[i] < minToRight[i])
                    beauty[i] = 2;
                beautySum += beauty[i];
            }
            return beautySum;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where n is length of array `nums`

-   [x] **Space Complexity :** O(n) where n is length of array `nums`

<hr>

**Approach 2 : Only 1 auxiliary array for precomputation :smile:**

-   We don't have to explicitly store the maximum element to left of each element.
-   We use only suffix array for pre-computation

=== "Java"

    ```java
    class Solution {
        public int sumOfBeauties(int[] nums) {
            int n = nums.length;
            int[] minToRight = new int[n];
            int beautySum = 0;

            int maxToLeft = nums[0];
            minToRight[n-1] = nums[n-1];

            for(int j = n - 2; j >= 0; --j)
                minToRight[j] = Math.min(minToRight[j + 1], nums[j + 1]);

            for(int i = 1; i < n - 1; ++i){

                if(maxToLeft < nums[i] && nums[i] < minToRight[i])
                    beautySum += 2;

                else if(nums[i - 1] < nums[i] && nums[i] < nums[i + 1])
                    beautySum += 1;

                maxToLeft = Math.max(maxToLeft, nums[i]);
            }
            return beautySum;
        }
    }
    ```

=== "C++"

    ```c++
    ```

-   [x] **Time Complexity :** O(n) where n is length of array `nums`

-   [x] **Space Complexity :** O(n) where n is length of array `nums`

```

```
