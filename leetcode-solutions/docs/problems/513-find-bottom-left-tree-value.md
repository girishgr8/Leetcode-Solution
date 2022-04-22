---
tags:
    - Tree
    - Depth-First Search
    - Breadth-First Search
    - Binary Tree
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/find-bottom-left-tree-value/](https://leetcode.com/problems/find-bottom-left-tree-value/){:target="\_blank"}

**Approach 1 : DFS :smile:**

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
        int maxHeight = -1;
        int bottomLeft = -1;
        public int findBottomLeftValue(TreeNode root) {
            solve(root, 0);
            return bottomLeft;
        }
        public void solve(TreeNode root, int currHeight){
            if(maxHeight < currHeight){
                maxHeight = currHeight;
                bottomLeft = root.val;
            }
            if(root.left != null)
                solve(root.left, currHeight + 1);
            if(root.right != null)
                solve(root.right, currHeight + 1);
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in the tree

-   [x] **Space Complexity :** O(n) where n = number of nodes in the tree
