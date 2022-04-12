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
        public int[] searchRange(int[] nums, int target) {
            int firstOccurrence = -1, lastOccurrence = -1;
            for(int i = 0; i < nums.length; i++){
                if(nums[i] == target){
                    if(firstOccurrence == -1)
                        firstOccurrence = lastOccurrence = i;
                    else
                        lastOccurrence = i;
                }
            }
            return new int[]{firstOccurrence, lastOccurrence};
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where _n_ are the length of the array

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : Modified Binary Search(Recursive) :smile:**

=== "Java"

    ```java
    class Solution {
        public int[] searchRange(int[] nums, int target) {
            int firstOccurrence = firstBS(nums, 0, nums.length-1, target);
            if(firstOccurrence != -1){
                int lastOccurrence = lastBS(nums, 0, nums.length-1, target);
                return new int[]{firstOccurrence, lastOccurrence};
            }
            return new int[]{-1, -1};
        }

        public int firstBS(int nums[], int low, int high, int target){
            if(low <= high){
                int mid = low + (high-low)/2;
                if(mid == 0 && nums[mid] == target)
                    return 0;
                if(nums[mid] == target && nums[mid-1] < target)
                    return mid;
                if(nums[mid] >= target)
                    return firstBS(nums, low, mid-1, target);
                else if(nums[mid] < target)
                    return firstBS(nums, mid+1, high, target);
            }
            return -1;
        }

        public int lastBS(int nums[], int low, int high, int target){
            if(low <= high){
                int mid = low + (high-low)/2;
                if(mid == nums.length-1 && nums[mid] == target)
                    return mid;
                if(nums[mid] == target && nums[mid+1] > target)
                    return mid;
                if(nums[mid] <= target)
                    return lastBS(nums, mid+1, high, target);
                else if(nums[mid] > target)
                    return lastBS(nums, low, mid-1, target);
            }
            return -1;
        }
    }
    ```

-   [x] **Time Complexity :** O(log n) where _n_ are the length of the array

-   [x] **Space Complexity :** O(log n) where _n_ are the length of the array

<hr>

**Approach 3 : Modified Binary Search(Iterative) :smile:**

=== "Java"

    ```java
    class Solution {
        public int[] searchRange(int[] nums, int target) {
            int firstOccurrence = firstBS(nums, 0, nums.length-1, target);
            if(firstOccurrence != -1){
                int lastOccurrence = lastBS(nums, 0, nums.length-1, target);
                return new int[]{firstOccurrence, lastOccurrence};
            }
            return new int[]{-1, -1};
        }

        public int firstBS(int nums[], int low, int high, int target){
            int idx = -1;
            while(low <= high){
                int mid = low + (high-low)/2;
                if(nums[mid] == target){
                    idx = mid;
                    high = mid - 1;
                }
                else if(nums[mid] > target)
                    high = mid - 1;
                else
                    low = mid + 1;
            }
            return idx;
        }

        public int lastBS(int nums[], int low, int high, int target){
            int idx = -1;
            while(low <= high){
                int mid = low + (high-low)/2;
                if(nums[mid] == target){
                    idx = mid;
                    low = mid + 1;
                }
                else if(nums[mid] > target)
                    high = mid - 1;
                else
                    low = mid + 1;
            }
            return idx;
        }
    }
    ```

-   [x] **Time Complexity :** O(log n) where _n_ are the length of the array

-   [x] **Space Complexity :** O(1)
