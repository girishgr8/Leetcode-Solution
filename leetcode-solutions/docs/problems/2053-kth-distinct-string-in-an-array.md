---
tags:
    - Array
    - Hash Table
    - String
    - Counting
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/kth-distinct-string-in-an-array/](https://leetcode.com/problems/kth-distinct-string-in-an-array/){:target="\_blank"}

**Approach : HashMap :smile:**

=== "Java"

    ```java
    class Solution {
        public String kthDistinct(String[] arr, int k) {
            Map<String,Integer> map = new LinkedHashMap<String,Integer>();
            for(String str: arr)
                map.put(str,map.getOrDefault(str,0)+1);
            int i = 0;
            for(String word: arr){
                if(map.getOrDefault(word,0) == 1 && ++i == k)
                    return word;
            }
            return "";
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = size of array

-   [x] **Space Complexity :** O(n1 + n2) where n = size of array
