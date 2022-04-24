---
tags:
    - String
    - Greedy
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/minimum-number-of-operations-to-convert-time/](https://leetcode.com/problems/minimum-number-of-operations-to-convert-time/){:target="\_blank"}

**Approach : Greedy :money_mouth:**

=== "Java"

    ```java
    class Solution {
        public int convertTime(String current, String correct) {
            int operations = 0;

            int currH = Integer.parseInt(current.split(":")[0]);
            int currM = Integer.parseInt(current.split(":")[1]);
            int corrH = Integer.parseInt(correct.split(":")[0]);
            int corrM = Integer.parseInt(correct.split(":")[1]);

            int totCurr = currH * 60 + currM;
            int totCorr = corrH * 60 + corrM;
            int diff = totCorr - totCurr;

            if(diff >= 60){
                operations += diff / 60;
                diff %= 60;
            }
            if(diff >= 15){
                operations += diff / 15;
                diff %= 15;
            }
            if(diff >= 5){
                operations += diff / 5;
                diff %= 5;
            }
            if(diff >= 1)
                operations += diff;

            return operations;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(1)

-   [x] **Space Complexity :** O(1)
