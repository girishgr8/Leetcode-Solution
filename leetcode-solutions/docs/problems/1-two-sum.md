---
tags:
    - Array
    - Hash Table
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/){:target="\_blank"}

**Approach 1 : Brute Force :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        public int[] twoSum(int[] nums, int target) {
            int n = nums.length;

            for(int i = 0; i < n;i++){
                for(int j = i + 1; j < n;j++)
                    if(nums[i] + nums[j] == target)
                        return new int[]{i, j};
            }

            return new int[]{-1, -1};
        }
    }
    ```

=== "C++"

    ``` c++
    class Solution {
    public:
        vector<int> twoSum(vector<int>& nums, int target) {
            int n = nums.size();

            for(int i = 0; i < n;i++){
                for(int j = i + 1; j < n;j++)
                    if(nums[i] + nums[j] == target)
                        return {i, j};
            }
            return {-1, -1};
        }
    };
    ```

-   [x] **Time Complexity :** O(n^2^) where _n_ is the length of array

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : HashTable Approach :smile:**

=== "Java"

    ```java
    public class Solution {
        public int[] twoSum(int[] nums, int target) {
            Map<Integer,Integer> map = new HashMap<Integer,Integer>();
            for(int i = 0; i < nums.length; i++){
                int n1 = nums[i];
                int n2 = target - n1;
                if(map.containsKey(n2)){
                    int result[] = new int[]{map.get(n2), i};
                    return result;
                }
                map.put(nums[i], i);
            }
            return new int[2];
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where _n_ is the length of array

-   [x] **Space Complexity :** O(n) where _n_ is the length of array
