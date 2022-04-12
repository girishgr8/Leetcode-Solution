---
tags:
    - Array
    - Binary Search
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/){:target="\_blank"}

**Approach 1 : Linear Search :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        public int findMin(int[] nums) {
            int n = nums.length;
            if(n == 1)
                return nums[0];
            // No rotations at all
            if(nums[0] <= nums[n-1])
                return nums[0];
            for(int i = 1; i < n; i++){
                int prev = (i + n - 1) % n;
                int next = (i + 1) % n;
                if(nums[i] <= nums[prev] && nums[i] <= nums[next])
                    return nums[i];
            }
            return nums[0];
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where _n_ are the length of the array

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : Modified Binary Search(Iterative) :smile:**

=== "Java"

    ```java
    class Solution {
        public int findMin(int[] nums) {
            int n = nums.length;
            int low = 0, high = n - 1;
            while(low <= high){
                // when array is already sorted
                if(nums[low] <= nums[high])
                    return nums[low];

                int mid = low + (high-low)/2;
                int next = (mid + 1) % n;
                int prev = (mid + n - 1) % n;

                // The minimum element has special characteristic in rotated array
                // that it is less than elements to its left and to its right
                if(nums[mid] <= nums[prev] && nums[mid] <= nums[next])
                    return nums[mid];

                // if the nums[low] <= nums[mid],
                // it means the subarray to left of mid is sorted
                // so minimum element lies in right subarray of mid
                else if(nums[low] <= nums[mid])
                    low = mid + 1;

                // if the nums[mid] <= nums[high],
                // it means the subarray to right of mid is sorted
                // so minimum element lies in left subarray of mid
                else if(nums[mid] <= nums[high])
                    high = mid - 1;
            }
            return -1;
        }

    }
    ```

-   [x] **Time Complexity :** O(log n) where _n_ are the length of the array

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 3: Modified Binary Search(Recursive) :smile:**

=== "Java"

    ```java
    class Solution {
        public int findMin(int[] nums) {
            return search(nums, 0, nums.length - 1);
        }
        public int search(int nums[], int low, int high){
            int n = nums.length;
            if(low <= high){
                // when array is already sorted
                if(nums[low] <= nums[high])
                    return nums[low];

                int mid = low + (high-low)/2;
                int next = (mid + 1) % n;
                int prev = (mid + n - 1) % n;

                // The minimum element has special characteristic in rotated array
                // that it is less than elements to its left and to its right
                if(nums[mid] <= nums[prev] && nums[mid] <= nums[next])
                    return nums[mid];

                // if the nums[low] <= nums[mid],
                // it means the subarray to left of mid is sorted
                // so minimum element lies in right subarray of mid
                else if(nums[low] <= nums[mid])
                    return search(nums, mid + 1, high);

                // if the nums[mid] <= nums[high],
                // it means the subarray to right of mid is sorted
                // so minimum element lies in left subarray of mid
                else if(nums[mid] <= nums[high])
                    return search(nums, low, mid - 1);
            }
            return -1;
        }
    }
    ```

-   [x] **Time Complexity :** O(log n) where _n_ are the length of the array

-   [x] **Space Complexity :** O(log n) where _n_ are the length of the array
