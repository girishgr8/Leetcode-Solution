---
tags:
    - Two Pointers
    - String
    - Recursion
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/reverse-string/](https://leetcode.com/problems/reverse-string/){:target="\_blank"}

**Approach 1: Recursive Approach**

=== "Java"

    ```java
    class Solution {
        public void reverseString(char[] s) {
            int i = 0;
            int j = s.length - 1;
            helper(s, i, j);
        }
        public void helper(char[] s, int i, int j){
            if(i > j) return;
            char temp = s[i];
            s[i] = s[j];
            s[j] = temp;
            helper(s, ++i, --j);
        }
    }
    ```

=== "C++"

    ```c++
    class Solution {
    public:
        void reverseString(vector<char>& s) {
            int i = 0;
            int j = s.size() - 1;

            while(i < j){
                char temp = s[i];
                s[i] = s[j];
                s[j] = temp;
                i++;
                j--;
            }
        }
    };
    ```

-   [x] **Time Complexity :** O(n) where _n_ is the length of string

-   [x] **Space Complexity :** O(n) where _n_ is the length of string

<hr>

**Approach 2: Iterative Approach**

=== "Java"

    ```java
    class Solution {
        public void reverseString(char[] s) {
            int i = 0, j = s.length - 1;
            while(i < j){
                char temp = s[i];
                s[i] = s[j];
                s[j] = t;
                i++;
                j--;
            }
        }
    }
    ```

=== "C++"

    ```c++
    class Solution {
    public:
        void reverseString(vector<char>& s) {
            int i = 0, j = s.size() - 1;
            while(i < j){
                char temp = s[i];
                s[i] = s[j];
                s[j] = temp;
                i++;
                j--;
            }
        }
    };
    ```

-   [x] **Time Complexity :** O(n) where _n_ is the length of string

-   [x] **Space Complexity :** O(1)
