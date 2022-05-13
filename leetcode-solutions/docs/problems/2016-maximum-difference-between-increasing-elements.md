---
tags:
    - Array
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/maximum-difference-between-increasing-elements/](https://leetcode.com/problems/maximum-difference-between-increasing-elements/){:target="\_blank"}

-   This problem is totally similar to [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/){:target="\_blank"}

**Approach 1 : Brute Force :sweat_smile:**

-   Idea is to try every pair of elements of the array `nums`, and check which combination gives maximum difference.

=== "Java"

    ```java
    class Solution {
        public int maximumDifference(int[] nums) {
            int n = nums.length;
            int maxDifference = -1;

            for(int i = 0; i < n - 1; i++){
                for(int j = i + 1; j < n; j++){
                    maxDifference = Math.max(maxDifference, nums[j] - nums[i]);
                }
            }
            return maxDifference == 0 ? -1 : maxDifference;
        }
    }
    ```

-   [x] **Time Complexity :** O(n^2^) where n is length of array `nums`

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : Dynamic Programming - Preprocessing :smile:**

-   By using extra space, for each index `i`, we pre-compute the maximum element value after `i`^`th`^ index

=== "Java"

    ```java
    class Solution {
        public int maximumDifference(int[] nums) {
            int n = nums.length;
            int maxDifference = -1;

            int largest[] = new int[n];
            largest[n-1] = nums[n-1];

            for(int i = n - 2; i >= 0; i--)
                largest[i] = Math.max(nums[i], largest[i + 1]);

            for(int i = 0; i < n; i++)
                maxDifference = Math.max(maxDifference, largest[i] - nums[i]);

            return maxDifference == 0 ? -1 : maxDifference;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where n is length of array `nums`

-   [x] **Space Complexity :** O(n) where n is length of array `nums`

<hr>

**Approach 3 : Best Approach :smile:**

-   Instead of storing the largest number towards right for each index `i`, we can simply check in single pass if the element at current index is greater than the largest element seen so far, if current one is highest, then we update the highest seen so far to nums[i], and calculate the maximum difference for that day.

=== "Java"

    ```java
    class Solution {
        public int maximumDifference(int[] nums) {
            int n = nums.length, maxDifference = 0;
            int highest = 0;

            for(int i = n - 1; i >= 0; i--){
                largest = Math.max(nums[i], largest);
                maxDifference = Math.max(maxDifference, largest - nums[i]);
            }
            return maxDifference == 0 ? -1 : maxDifference;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where n is length of array `nums`

-   [x] **Space Complexity :** O(1)
