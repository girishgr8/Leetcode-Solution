---
tags:
    - Array
    - Binary Search
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/kth-missing-positive-number/](https://leetcode.com/problems/kth-missing-positive-number/){:target="\_blank"}

**Approach : Modified Binary Search :smile:**

=== "Java"

    ```java
    class Solution {
        public int findKthPositive(int[] arr, int k) {
            int low = 0, high = arr.length;
            while(low < high){
            int mid = low + (high-low)/2;
                if(arr[mid] - mid - 1 < k)
                    low = mid + 1;
                else
                    high = mid;
            }
            return high + k;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(log n) where n = number of elements in array

-   [x] **Space Complexity :** O(1)
