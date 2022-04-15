---
tags:
    - Array
    - Backtracking
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/combination-sum-iii/](https://leetcode.com/problems/combination-sum-iii/){:target="\_blank"}

**Approach : Backtracking :smile:**

=== "Java"

    ```java
    class Solution {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        public List<List<Integer>> combinationSum3(int k, int n) {
            int min = k*(k+1)/2;
            int max = 9*(9+1)/2;
            if(min > n || max < n) return result;
            for(int i = 1; i <= 9; i++){
                List<Integer> list = new ArrayList<Integer>();
                list.add(i);
                find(i, k-1, n-i, list);
            }
            return result;
        }

        public void find(int curr, int k, int n, List<Integer> list){
            // base case:
            // if we used more than 'k' numbers OR their sum has exceeded 'n'
            if(n < 0 || k < 0)
                return;
            // if 'k' used numbers sum up exactly to 'n'
            if(n == 0 && k == 0){
                result.add(new ArrayList<Integer>(list));
                return;
            }
            // recursively solve for starting from next number
            // since we cannot use a number twice
            for(int i = curr + 1; i <= 9; i++){
                list.add(i);
                find(i,k-1,n-i,list);
                list.remove(new Integer(i));
            }
            return;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** ~O(1) since the constraints are small

-   [x] **Space Complexity :** ~O(1) since the constraints are small
