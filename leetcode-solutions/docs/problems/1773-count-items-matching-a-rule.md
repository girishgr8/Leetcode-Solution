**Leetcode Problem Link :**

[https://leetcode.com/problems/count-items-matching-a-rule/](https://leetcode.com/problems/count-items-matching-a-rule/){:target="\_blank"}

=== "Java"

    ```java
    class Solution {
        public int countMatches(List<List<String>> items, String ruleKey, String ruleValue) {
            int key = ruleKey.equals("type") ? 0 : (ruleKey.equals("color") ? 1 : 2);
            int size = items.size();
            int count = 0;
            for(int i = 0; i < size; i++){
                if(items.get(i).get(key).equals(ruleValue))
                    count++;
            }
            return count;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where n is the number of items

-   [x] **Space Complexity :** O(1)
