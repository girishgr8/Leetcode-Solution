---
tags:
    - Math
    - String
    - Simulation
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/complex-number-multiplication/](https://leetcode.com/problems/complex-number-multiplication/){:target="\_blank"}

**Approach : Formula Simulation :smile:**

=== "Java"

    ```java
    class Solution {
        public String complexNumberMultiply(String num1, String num2) {
            // e.g. nums1 = 1+1i,  nums2 = 1+-1i
            // n1 = ["1", "1i"],   n2 = ["1", "-1i"]
            String[] n1 = num1.split("\\+");
            String[] n2 = num2.split("\\+");
            // r1 = 1, r2 = 1
            // c1 = 1, c2 = -1
            // for c1, c2 ==> take 2nd part of splitted string from 0th index to second last index
            // this will exclude 'i' from the splitted string to get actual complex part
            int r1 = Integer.parseInt(n1[0]);
            int r2 = Integer.parseInt(n2[0]);
            int c1 = Integer.parseInt(n1[1].substring(0, n1[1].length()-1));
            int c2 = Integer.parseInt(n2[1].substring(0, n2[1].length()-1));
            int real = r1*r2 + (c1*c2*-1);
            int complex = r1*c2 + r2*c1;
            String result = Integer.toString(real) + "+" + Integer.toString(complex) + "i";
            return result;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(1)

-   [x] **Space Complexity :** O(1)
