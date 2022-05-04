---
tags:
    - Array
    - Hash Table
    - Two Pointers
    - Sorting
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/max-number-of-k-sum-pairs/](https://leetcode.com/problems/max-number-of-k-sum-pairs/){:target="\_blank"}

**Approach : Sorting + Two Pointers Approach :smile:**

=== "Java"

    ```java
    class Solution {
        public int maxOperations(int[] nums, int k) {
            int n = nums.length;
            int count = 0;
            // initialise left & right pointers
            // left ptr points to smaller values of array
            // right ptr points to larger values of array
            int l = 0, r = n - 1;
            // sort the array
            Arrays.sort(nums);

            while(l < r){
                // if nums[l]+nums[r] sum upto k, then we found a pair,
                // increment count
                // increment left ptr & decrement right ptr
                if(nums[l] + nums[r] == k){
                    count++;
                    l++;
                    r--;
                }
                // if nums[l]+nums[r] is less than k
                // then we have to increment left ptr
                // as we need to have some bigger value, so that it equals to 'k'
                else if(nums[l] + nums[r] < k)
                    l++;
                // if nums[l]+nums[r] is greater than k
                // then we have to decrement right ptr
                // as we need to have some smaller value, so that it equals to 'k'
                else
                    r--;
            }
            return count;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(nlogn) where n = length of array `nums`

-   [x] **Space Complexity :** O(1)
