---
tags:
    - Array
    - Hash Table
    - String
    - Counting
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/count-common-words-with-one-occurrence/](https://leetcode.com/problems/count-common-words-with-one-occurrence/){:target="\_blank"}

**Approach : HashMap :smile:**

=== "Java"

    ```java
    class Solution {
        public int countWords(String[] words1, String[] words2) {
            Map<String,Integer> map1 = new HashMap<String,Integer>();
            Map<String,Integer> map2 = new HashMap<String,Integer>();

            for(String word: words1)
                map1.put(word,map1.getOrDefault(word,0)+1);

            for(String word: words2)
                map2.put(word,map2.getOrDefault(word,0)+1);

            int unique = 0;
            for(String word: map1.keySet()){
                int n1 = map1.get(word);
                int n2 = map2.getOrDefault(word,0);
                if(n1==1 && n2==1)
                    unique++;
            }
            return unique;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n1 + n2) where n1 = size of word1 array, n2 = size of word2 array

-   [x] **Space Complexity :** O(n1 + n2) where n1 = size of word1 array, n2 = size of word2 array
