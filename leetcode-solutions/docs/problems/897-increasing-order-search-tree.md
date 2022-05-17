---
tags:
    - Stack
    - Tree
    - Depth-First Search
    - Binary Search Tree
    - Binary Tree
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/increasing-order-search-tree/](https://leetcode.com/problems/increasing-order-search-tree/){:target="\_blank"}

**Approach : Recursion :smile:**

-   Perform simple inorder traversal and take help of dummy node

=== "Java"

    ```java
    /**
    * Definition for a binary tree node.
    * public class TreeNode {
    *     int val;
    *     TreeNode left;
    *     TreeNode right;
    *     TreeNode(int x) { val = x; }
    * }
    */
    class Solution {
        TreeNode dummy = new TreeNode(0);
        public TreeNode increasingBST(TreeNode root) {
            TreeNode head = dummy;
            inorder(root);
            return head.right;
        }
        public void inorder(TreeNode root){
            if(root == null)
                return;
            inorder(root.left);

            root.left = null;
            dummy.right = root;
            dummy = root;

            inorder(root.right);
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in the tree

-   [x] **Space Complexity :** O(1)
