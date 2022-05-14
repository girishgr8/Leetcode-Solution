---
tags:
    - Math
    - String
    - Greedy
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/largest-odd-number-in-string/](https://leetcode.com/problems/largest-odd-number-in-string/){:target="\_blank"}

**Approach : Intuitive :smile:**

=== "Java"

    ```java
    class Solution {
        public String largestOddNumber(String num) {
            int n = num.length();
            // start search from last digit of string
            // if it is odd then return substring from 0 to curr_idx + 1
            for(int i = n - 1; i >= 0; i--){
                if((num.charAt(i) - '0') % 2 == 1)
                    return num.substring(0, i + 1);
            }
            return "";
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = length of string `num`

-   [x] **Space Complexity :** O(1)
