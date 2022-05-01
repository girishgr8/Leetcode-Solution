---
tags:
    - Two Pointers
    - String
    - Stack
    - Simulation
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/backspace-string-compare/](https://leetcode.com/problems/backspace-string-compare/){:target="\_blank"}

**Approach : Simulation + Stack :smile:**

=== "Java"

    ```java
    class Solution {
        public boolean backspaceCompare(String s, String t) {
            int len1 = s.length(), len2 = t.length();
            int i = 0, j = 0;
            Stack<Character> stack1 = new Stack<Character>();
            Stack<Character> stack2 = new Stack<Character>();
            while(i < len1){
                if(s.charAt(i) != '#')
                    stack1.push(s.charAt(i));

                else if(!stack1.isEmpty())
                    stack1.pop();
                i++;
            }

            while(j < len2){
                if(t.charAt(j) != '#')
                    stack2.push(t.charAt(j));

                else if(!stack2.isEmpty())
                    stack2.pop();
                j++;
            }
            while(!stack1.isEmpty() && !stack2.isEmpty()){
                if(stack1.pop() != stack2.pop())
                    return false;
            }
            if(!stack1.isEmpty()) return false;
            if(!stack2.isEmpty()) return false;
            return true;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(m + n) where m and n are the lengths of string `s` and `t`

-   [x] **Space Complexity :** O(m + n) where m and n are the lengths of string `s` and `t`
