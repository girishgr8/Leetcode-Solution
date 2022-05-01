---
tags:
    - Array
    - Depth-First Search
    - Breadth-First Search
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/jump-game-iii/](https://leetcode.com/problems/jump-game-iii/){:target="\_blank"}

**Approach : Depth First Search :smile:**

=== "Java"

    ```java
    class Solution {
        boolean[] visited;
        public boolean canReach(int[] arr, int start) {
            if(arr[start] == 0) return true;
            visited = new boolean[arr.length];
            return jump(arr, start);
        }

        public boolean jump(int arr[], int c){
            int n = arr.length;
            // if we have reached an index with value 0, then return true
            if(arr[c] == 0)
                return true;

            // mark the index as visited, otherwise we may fall into infinite loop
            visited[c] = true;

            // initialise boolean variable 'reach' as false
            // which will keep track whether we can reach an index with value '0'
            // from the current index
            boolean reach = false;

            // l & r are left are right jump indices
            int r = c + arr[c];
            int l = c - arr[c];

            // if right jump is within bounds & if we have not visited it
            // then jump on the right index
            if(r < n && !visited[r])
                reach = reach || jump(arr, r);

            // if by making a right jump, we reached to some index with value '0'
            // then no need to check by making left jump
            if(reach) return true;

            // if left jump is within bounds & if we have not visited it
            // then jump on the left index
            if(l >= 0 && !visited[l])
                reach = reach || jump(arr, l);

            // rollback and check for other indices & return reach
            visited[c] = false;
            return reach;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = length of array `arr`

-   [x] **Space Complexity :** O(n) where n = length of array `arr`
