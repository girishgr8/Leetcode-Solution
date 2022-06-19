---
tags:
    - Hash Table
    - String
    - Queue
    - Counting
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/first-unique-character-in-a-string/](https://leetcode.com/problems/first-unique-character-in-a-string/){:target="\_blank"}

**Approach : HashMap Approach :smile:**

=== "Java"

    ```java
    class Solution {
        public int firstUniqChar(String s) {
            int[] map = new int[26];
            int n = s.length();
            for(int i = 0; i < n; i++){
                map[s.charAt(i)-'a'] += 1;
            }
            for(int i = 0; i < n; i++){
                if(map[s.charAt(i)-'a'] == 1)
                    return i;
            }
            return -1;
        }
    }
    ```

=== "C++"

    ``` c++
    class Solution {
    public:
        int firstUniqChar(string s) {
            int map[26] = {0};
            int n = s.size();
            for(int i = 0; i < n; i++){
                map[s[i]-'a'] += 1;
            }
            for(int i = 0; i < n; i++){
                if(map[s[i]-'a'] == 1)
                    return i;
            }
            return -1;
        }
    };
    ```

-   [x] **Time Complexity :** O(n) where n = length of string

-   [x] **Space Complexity :** O(1), as the map will contain maximum 26 characters
