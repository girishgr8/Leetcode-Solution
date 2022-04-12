---
tags:
    - Array
    - Hash Table
    - Math
    - Bit Manipulation
    - Sorting
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/missing-number/](https://leetcode.com/problems/missing-number/){:target="\_blank"}

**Approach 1: Sorting & linear search :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        public int missingNumber(int[] nums) {
            Arrays.sort(nums);
            int n = nums.length;
            for(int i = 0; i < n; i++){
                if(nums[i] != i)
                    return i;
            }
            return n;
        }
    }
    ```

=== "C++"

    ```c++
    class Solution {
    public:
        int missingNumber(vector<int>& nums) {
            sort(nums.begin(), nums.end());
            int n = nums.size();
            for(int i = 0; i < n; i++){
                if(nums[i] != i)
                    return i;
            }
            return n;
        }
    };
    ```

-   [x] **Time Complexity :** O(nlogn) where _n_ is length of array

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2: Using sum of first _n_ natural numbers property :slight_smile:**

=== "Java"

    ```java
    class Solution {
        public int missingNumber(int[] nums) {
            int n = nums.length;
            int result = n*(n+1)/2;
            for(int i = 0; i < n; i++){
                result -= nums[i];
            }
            return result;
        }
    }
    ```

=== "C++"

    ```c++
    class Solution {
    public:
        int missingNumber(vector<int>& nums) {
            int n = nums.size();
            int result = n*(n+1)/2;
            for(int i = 0; i < n; i++){
                result -= nums[i];
            }
            return result;
        }
    };
    ```

-   [x] **Time Complexity :** O(n) where _n_ is length of array

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 3: Using XOR of the numbers :smiley:**

=== "Java"

    ```java
    class Solution {
        public int missingNumber(int[] nums) {
            int result = nums.length;
            for(int i = 0; i < nums.length; i++){
                result ^= i;
                result ^= nums[i];
            }
            return result;
        }
    }
    ```

=== "C++"

    ```c++
    class Solution {
    public:
        int missingNumber(vector<int>& nums) {
            int result = nums.size();
            for(int i = 0; i < nums.size(); i++){
                result ^= i;
                result ^= nums[i];
            }
            return result;
        }
    };
    ```

-   [x] **Time Complexity :** O(n) where _n_ is length of array

-   [x] **Space Complexity :** O(1)
