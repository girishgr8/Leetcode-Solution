---
tags:
    - Array
    - Binary Search
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/find-smallest-letter-greater-than-target/](https://leetcode.com/problems/find-smallest-letter-greater-than-target/){:target="\_blank"}

**Approach 1 : Linear Search :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        public char nextGreatestLetter(char[] letters, char target) {
            for(char c : letters){
                if(c > target)
                    return c;
            }
            return letters[0];
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = length of array `letters`

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : Binary Search :smile:**

=== "Java"

    ```java
    class Solution {
        public char nextGreatestLetter(char[] letters, char target) {
            int n = letters.length;
            int low = 0, high = n - 1;
            char greater = '\0';

            while(low <= high){
                int mid = low + (high - low) / 2;

                if(letters[mid] > target){
                    greater = letters[mid];
                    high = mid - 1;
                }
                else
                    low = mid + 1;
            }
            return (greater == '\0' ? letters[0] : greater);
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(log n) where n = length of array `letters`

-   [x] **Space Complexity :** O(1)
