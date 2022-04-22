---
tags:
    - Backtracking
    - Breadth-First Search
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/numbers-with-same-consecutive-differences/](https://leetcode.com/problems/numbers-with-same-consecutive-differences/){:target="\_blank"}

**Approach : DFS + Backtracking :smile:**

=== "Java"

    ```java
    class Solution {
        public int[] numsSameConsecDiff(int n, int k) {
            List<Integer> answer = new ArrayList<Integer>();
            for(int i = 1; i <= 9; i++){
                helper(i, n - 1, k, answer, 0);
            }
            int size = answer.size();
            int[] result = new int[size];
            for(int i = 0; i < size; i++)
                result[i] = answer.get(i);
            return result;
        }

        public void helper(int d, int n, int k, List<Integer> answer, int number){
            number = number * 10 + d;
            if(n == 0){
                answer.add(number);
                return;
            }
            int c1 = d + k;
            int c2 = d - k;
            if(c1 <= 9)
                helper(c1, n - 1, k, answer, number);
            if(c1 != c2 && c2 >= 0)
                helper(c2, n - 1, k, answer, number);
            return;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in the tree

-   [x] **Space Complexity :** O(n) where n = number of nodes in the tree
