---
tags:
    - Tree
    - Depth-First Search
    - Breadth-First Search
    - Binary Tree
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/maximum-level-sum-of-a-binary-tree/](https://leetcode.com/problems/maximum-level-sum-of-a-binary-tree/){:target="\_blank"}

**Approach : Depth-First Search + HashMap :smile:**

=== "Java"

    ```java
    /**
    * Definition for a binary tree node.
    * public class TreeNode {
    *     int val;
    *     TreeNode left;
    *     TreeNode right;
    *     TreeNode() {}
    *     TreeNode(int val) { this.val = val; }
    *     TreeNode(int val, TreeNode left, TreeNode right) {
    *         this.val = val;
    *         this.left = left;
    *         this.right = right;
    *     }
    * }
    */
    class Solution {
        Map<Integer,Integer> map;
        public int maxLevelSum(TreeNode root) {
            map = new HashMap<Integer,Integer>();
            int minLevel = Integer.MAX_VALUE, maxSum = Integer.MIN_VALUE;
            helper(1, root);
            for(Integer level : map.keySet()){
                int sum = map.get(level);
                if(sum > maxSum){
                    minLevel = level;
                    maxSum = sum;
                }
            }
            return minLevel;
        }

        public void helper(int h, TreeNode root){
            if(root == null)
                return;
            map.put(h, map.getOrDefault(h, 0) + root.val);
            helper(h + 1, root.left);
            helper(h + 1, root.right);
            return;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in the tree

-   [x] **Space Complexity :** O(n) where n = number of nodes in the tree
