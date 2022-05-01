---
tags:
    - Array
    - HashTable
    - Math
    - Prefix Sum
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/continuous-subarray-sum/](https://leetcode.com/problems/continuous-subarray-sum/){:target="\_blank"}

**Approach 1 : Naive Approach (Time Limit Exceeded) :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        public boolean checkSubarraySum(int[] nums, int k) {
            for(int i = 0; i < nums.length - 1; i++){
                int sum = nums[i];
                for(int j = i + 1; j < nums.length; j++){
                    sum += nums[j];
                    if(sum % k == 0)
                        return true;
                }
            }
            return false;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n^2^) where n = length of array `nums`

-   [x] **Space Complexity :** O(1) where n = length of array `nums`

<hr>

**Approach 2 : HashMap + Math trick :smile:**

=== "Java"

    ```java
    class Solution {
        public boolean checkSubarraySum(int[] nums, int k) {
            int mod = 0, n = nums.length;
            Map<Integer, Integer> map = new HashMap();
            map.put(0, -1);

            for(int i = 0; i < n; i++){
                mod = (mod + nums[i]) % k;
                if(map.containsKey(mod) && i-map.get(mod) > 1) return true;
                if(!map.containsKey(mod))
                    map.put(mod,i);
            }

            return false;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = length of array `nums`

-   [x] **Space Complexity :** O(n) where n = length of array `nums`
