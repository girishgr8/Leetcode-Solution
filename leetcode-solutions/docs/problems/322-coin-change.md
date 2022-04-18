---
tags:
    - Array
    - Dynamic Programming
    - Breadth-First Search
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/kth-smallest-element-in-a-bst/](https://leetcode.com/problems/kth-smallest-element-in-a-bst/){:target="\_blank"}

**Approach 3 : Bottom-Up Approach :smile:**

=== "Java"

    ```java
    class Solution {
        public int coinChange(int[] coins, int amount) {
            int[] dp = new int[amount + 1];
            int max = Integer.MAX_VALUE;
            Arrays.fill(dp, max);
            dp[0] = 0;
            for(int i = 1; i < dp.length; i++){
                for(int j = 0; j < coins.length; j++){
                    if(coins[j] <= i){
                        int min = dp[i-coins[j]];
                        if(min != max && min + 1 < dp[i])
                            dp[i] = min + 1;
                    }
                }
            }
            return dp[amount] != max ? dp[amount] : -1;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in BST

-   [x] **Space Complexity :** O(n) where n = number of nodes in BST
