---
tags:
    - String
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/check-if-word-equals-summation-of-two-words/](https://leetcode.com/problems/check-if-word-equals-summation-of-two-words/){:target="\_blank"}

**Approach : Formula Simulation :smile:**

=== "Java"

    ```java
    class Solution {
        public boolean isSumEqual(String firstWord, String secondWord, String targetWord) {
            int val1 = findValue(firstWord);
            int val2 = findValue(secondWord);
            int val3 = findValue(targetWord);
            return ((val1 + val2) == val3);
        }

        public int findValue(String word){
            int val = 0;
            for(int i = 0; i < word.length(); i++)
                val = 10 * val + (word.charAt(i) - 'a');
            return val;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(1) as each word's length is maximum 8 characters

-   [x] **Space Complexity :** O(1)
