---
tags:
    - Array
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/partition-array-into-disjoint-intervals/](https://leetcode.com/problems/partition-array-into-disjoint-intervals/){:target="\_blank"}

**Approach 1 : Prefix & Suffix arrays for precomputation :sweat_smile:**

-   Idea is pre-compute maximum element to its left and minimum element to its right for each element the array `nums`.
-   We can use suffix & prefix arrays.
-   `prefix[i]` will store maximum values from `[0, i-1]`
-   `suffix[i]` will store minimum values from `[i, n-1]`
-   This approach to this problem is almost same as [2012. Sum of Beauty in the Array](https://leetcode.com/problems/sum-of-beauty-in-the-array/){:target="\_blank"}

=== "Java"

    ```java
    class Solution {
        public int partitionDisjoint(int[] nums) {
            int n = nums.length;
            int[] maxToLeft = new int[n];
            int[] minToRight = new int[n];

            maxToLeft[0] = nums[0];
            minToRight[n - 1] = nums[n - 1];

            for(int i = 1, j = n - i; i < n; ++i, --j){
                maxToLeft[i] = Math.max(maxToLeft[i - 1], nums[i - 1]);
                minToRight[j - 1] = Math.min(minToRight[j], nums[j - 1]);
            }

            for(int i = 1; i < n; ++i){
                if(maxToLeft[i] <= minToRight[i])
                    return i;
            }
            return -1;
        }
    }
    ```

=== "C++"

    ```c++
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
        public int partitionDisjoint(int[] nums) {
            int n = nums.length;
            int[] minToRight = new int[n];

            int maxToLeft = nums[0];
            minToRight[n - 1] = nums[n - 1];

            for(int j = n - 2; j >= 0; --j)
                minToRight[j] = Math.min(minToRight[j + 1], nums[j]);

            for(int i = 1; i < n; ++i){

                if(maxToLeft <= minToRight[i])
                    return i;

                maxToLeft = Math.max(maxToLeft, nums[i]);
            }
            return -1;
        }
    }
    ```

=== "C++"

    ```c++
    ```

-   [x] **Time Complexity :** O(n) where n is length of array `nums`

-   [x] **Space Complexity :** O(n) where n is length of array `nums`

<hr>

**Approach 3 : No extra space :smile:**

=== "Java"

    ```java
    class Solution {
        public int partitionDisjoint(int[] nums) {
            int n = nums.length;
            int max = nums[0];
            int currMax = nums[0];
            int size = 1;

            for(int i = 1; i < n; ++i){
                if(nums[i] < max){
                    size = i + 1;
                    max = currMax;
                }
                else{
                    currMax = Math.max(currMax, nums[i]);
                }
            }
            return size;
        }
    }
    ```

=== "C++"

    ```c++
    ```

-   [x] **Time Complexity :** O(n) where n is length of array `nums`

-   [x] **Space Complexity :** O(1)
