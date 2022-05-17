---
tags:
    - Hash Table
    - String
    - Backtracking
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/letter-combinations-of-a-phone-number/](https://leetcode.com/problems/letter-combinations-of-a-phone-number/){:target="\_blank"}

**Approach : Backtracking :smile:**

=== "Java"

    ```java
    class Solution {
        Map<Character,String> map;
        public List<String> letterCombinations(String digits) {
            List<String> result = new ArrayList<String>();
            map = new HashMap<Character,String>();
            map.put('2', "abc");
            map.put('3', "def");
            map.put('4', "ghi");
            map.put('5', "jkl");
            map.put('6', "mno");
            map.put('7', "pqrs");
            map.put('8', "tuv");
            map.put('9', "wxyz");

            if(digits.length() == 0)
                return result;

            solve(digits, 0, digits.length(), new ArrayList<Character>(), result);
            return result;

        }

        public void solve(String digits, int i, int n, List<Character> list, List<String> result){
            // if we used all the digits from given 'digits' string
            if(i >= n){
                StringBuilder sb = new StringBuilder();
                for (Character ch : list) sb.append(ch);
                result.add(sb.toString());
                return;
            }
            // get the letters corresponding to each digit
            String letters = map.get(digits.charAt(i));

            // add each letter corresponding to each digit to result
            // recursively solve for next digit of the 'digits' string
            for(int j = 0; j < letters.length(); ++j){
                // add one letter mapped to current digit
                list.add(letters.charAt(j));
                // recursively solve for remaining digits of string
                solve(digits, i + 1, n, list, result);
                // remove the added letter mapped to current digit (rollback)
                list.remove(list.size() - 1);
            }
            return;
        }
    }
    ```

=== "C++"

    ```c++
    ```

-   [x] **Time Complexity :**

-   [x] **Space Complexity :**
