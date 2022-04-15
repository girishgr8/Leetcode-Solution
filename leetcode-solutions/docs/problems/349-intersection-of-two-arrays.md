---
tags:
    - Array
    - Hash Table
    - Two Pointers
    - Binary Search
    - Sorting
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/intersection-of-two-arrays/](https://leetcode.com/problems/intersection-of-two-arrays/){:target="\_blank"}

**Approach : Sorting + Binary Search :smile:**

=== "Java"

    ```java
    class Solution {
        public int[] intersection(int[] nums1, int[] nums2) {
            int n1 = nums1.length, n2 = nums2.length, i = 0;
            Set<Integer> set = new HashSet<Integer>();
            int[] baseArr, searchArr;
            Arrays.sort(nums1);
            Arrays.sort(nums2);
            if(n1 < n2){
                baseArr = nums1;
                searchArr = nums2;
            }
            else{
                baseArr = nums2;
                searchArr = nums1;
            }
            for(int n: baseArr){
                if(find(searchArr, n))
                    set.add(n);
            }
            int result[] = new int[set.size()];
            Iterator<Integer> it = set.iterator();
            while(it.hasNext())
                result[i++] = it.next();
            return result;
        }

        public boolean find(int nums[], int target){
            int low = 0, high = nums.length - 1;
            while(low <= high){
                int mid = low + (high-low)/2;
                if(nums[mid] == target)
                    return true;
                else if(nums[mid] > target)
                    high = mid - 1;
                else
                    low = mid + 1;
            }
            return false;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(nlogn + mlogm + nlogm) where n & m are size of arrays nums1 and nums2

-   [x] **Space Complexity :** O(max(n, m)) where n & m are size of arrays nums1 and nums2
