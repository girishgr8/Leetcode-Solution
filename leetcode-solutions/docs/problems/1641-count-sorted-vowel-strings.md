---
tags:
    - Dynamic Programming
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/count-sorted-vowel-strings/](https://leetcode.com/problems/count-sorted-vowel-strings/){:target="\_blank"}

**Approach 1 : Brute Force :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        int count = 0;
        public int countVowelStrings(int n) {
            for(int i = 0; i < 5; i++)
                generate(i, n - 1);
            return count;
        }

        public void generate(int v, int n){
            // base case
            if(n == 0){
                count++;
                return;
            }

            for(int i = v; i < 5; i++)
                generate(i, n - 1);

            return;
        }
    }
    ```

=== "C++"

    ```c++
    ```

-   [x] **Time Complexity :**

-   [x] **Space Complexity :**

<hr>

**Approach 2 : Dynamic Programming :smile:**

-   For n = 1, strings with first letter as [a,e,i,o,u] are {a:1, e:1, i:1, o:1, u:1}. These strings are as follows:

    -   'a': {a}
    -   'e': {e}
    -   'i': {i}
    -   'o': {o}
    -   'u': {u}

-   For n = 2, strings with first letter as [a,e,i,o,u] are {a:5, e:4, i:3, o:2, u:1}. These strings are as follows:

    -   'a' : {aa, ae, ai, ao, au}
    -   'e' : {ee, ei, eo, eu}
    -   'i' : {ii, io, iu}
    -   'o' : {oo, ou}
    -   'u' : {uu}

-   For n = 3, strings with first letter as [a,e,i,o,u] are {a:15, e:10, i:6, o:3, u:1}. These strings are as follows:

    -   'a' : {aaa, aae, aai, aao, aau, aee, aei, aeo, aeu, aii, aio, aiu, aoo, aou, auu}
    -   'e' : {eee, eei, eeo, eeu, eii, eio, eiu, eoo, eou, euu}
    -   'i' : {iii, iio, iiu, ioo, iou, iuu}
    -   'o' : {ooo, oou, ouu}
    -   'u' : {uuu}

    === "Java"

        ```java
        class Solution {
            public int countVowelStrings(int n) {
                int[] dp = new int[5];
                Arrays.fill(dp, 1);
                while(n-- > 0){
                    for(int i = 3; i >= 0; i--)
                        dp[i] += dp[i + 1];
                }
                return dp[0];
            }
        }
        ```

=== "C++"

    ```c++
    ```

-   [x] **Time Complexity :** O(n) where n is the length of string

-   [x] **Space Complexity :** O(1)
