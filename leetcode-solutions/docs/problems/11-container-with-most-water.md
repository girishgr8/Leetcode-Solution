---
tags:
    - Array
    - Two Pointers
    - Greedy
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/container-with-most-water/](https://leetcode.com/problems/container-with-most-water/){:target="\_blank"}

**Approach 1 : Brute Force :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        public int maxArea(int[] height) {
            int n = height.length;
            int max = 0;
            for(int i = 0; i < n; i++){
                for(int j = i + 1; j < n; j++){
                    int x = j - i;
                    int y = Math.min(height[i], height[j]);
                    max = Math.max(max, x * y);
                }
            }
            return max;
        }
    }
    ```

-   [x] **Time Complexity :** O(n^2^) where _n_ is the length of array

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : Two Pointers :smile:**

=== "Java"

    ```java
    class Solution {
        public int maxArea(int[] height) {
            int n = height.length;
            int left = 0, right = n - 1;
            int max = 0;
            while(left < right){
                int x = right - left;
                int y = Math.min(height[left], height[right]);
                max = Math.max(max, x * y);
                if(height[left] < height[right])
                    left++;
                else
                    right--;
            }
            return max;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where _n_ is the length of array

-   [x] **Space Complexity :** O(1)
