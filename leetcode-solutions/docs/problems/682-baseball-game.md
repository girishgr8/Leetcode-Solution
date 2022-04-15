---
tags:
    - Array
    - Stack
    - Simulation
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/baseball-game/](https://leetcode.com/problems/baseball-game/){:target="\_blank"}

**Approach : Simulation :smile:**

=== "Java"

    ```java
    class Solution {
        public int calPoints(String[] ops) {
            List<Integer> list = new ArrayList<Integer>();
            int size = 0, sum = 0;
            for(String op: ops){
                if(op.equals("C"))
                    list.remove(--size);
                else if(op.equals("D")){
                    list.add(list.get(size-1)*2);
                    size++;
                }
                else if(op.equals("+")){
                    list.add(list.get(size-1) + list.get(size-2));
                    size++;
                }
                else{
                    list.add(new Integer(op));
                    size++;
                }
            }
            for(Integer i: list)
                sum += i;
            return sum;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of operations

-   [x] **Space Complexity :** O(n) where n = number of operations
