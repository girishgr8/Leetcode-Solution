---
tags:
    - Backtracking
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/combinations/](https://leetcode.com/problems/combinations/){:target="\_blank"}

**Approach : Backtracking :smile:**

=== "Java"

    ```java
    class Solution {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        public List<List<Integer>> combine(int n, int k) {
            for(int i = 1; i <= n; i++){
                List<Integer> list = new ArrayList<Integer>();
                list.add(i);
                solve(i, n, k-1, list);
            }
            return result;
        }

        public void solve(int curr, int n, int k, List<Integer> list){
            if(k < 0)
                return;
            if(k == 0){
                result.add(new ArrayList<Integer>(list));
                return;
            }
            for(int i = curr+1; i <= n; i++){
                list.add(i);
                solve(i, n, k-1, list);
                list.remove(new Integer(i));
            }
        }
    }
    ```

=== "C++"

    ```c++

    ```

-   [x] **Time Complexity :**

-   [x] **Space Complexity :**
