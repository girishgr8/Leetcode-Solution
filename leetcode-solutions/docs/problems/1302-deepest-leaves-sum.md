---
tags:
    - Tree
    - Depth-First Search
    - Breadth-First Search
    - Binary Tree
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/deepest-leaves-sum/](https://leetcode.com/problems/deepest-leaves-sum/){:target="\_blank"}

**Approach : Depth-First Search :smile:**

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
        int maxDepth = 0, sum = 0;

        public int deepestLeavesSum(TreeNode root) {
            findSum(root, 0);
            return sum;
        }

        private void findSum(TreeNode root, int depth){
            if(root == null) return;

            // if the depth of current node is greater than maximum depth seen till now
            // then reset sum equal to value of current node
            // update maxDepth to current node's depth
            if(maxDepth < depth){
                sum = root.val;
                maxDepth = depth;
            }

            // if the depth of current node is equal to than maximum depth seen till now
            // then add current node's value to the sum
            else if(maxDepth == depth)
                sum += root.val;

            // recursively solve for left subtree
            findSum(root.left, depth + 1);
            // recursively solve for right subtree
            findSum(root.right, depth + 1);
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in tree

-   [x] **Space Complexity :** O(h) where h = height of tree
