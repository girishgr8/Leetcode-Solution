---
tags:
    - Tree
    - Binary Search Tree
    - Binary Tree
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/search-in-a-binary-search-tree/](https://leetcode.com/problems/search-in-a-binary-search-tree/){:target="\_blank"}

**Approach : Recursion :smile:**

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
        public TreeNode searchBST(TreeNode root, int val) {
            // if root is null, then return null
            if(root == null) return null;
            // if root's val matches val, then return root
            if(root.val == val)
                return root;
            // if root's val is greater than val,
            // so the target node will be in left subtree of root
            if(root.val > val)
                return searchBST(root.left, val);
            // otherwise, it means root's val is less than val,
            // so the target node will be in left subtree of root
            else
                return searchBST(root.right, val);
        }
    }
    ```

=== "C++"

    ``` c++
    /**
    * Definition for a binary tree node.
    * struct TreeNode {
    *     int val;
    *     TreeNode *left;
    *     TreeNode *right;
    *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
    *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
    *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
    * };
    */
    class Solution {
    public:
        TreeNode* searchBST(TreeNode* root, int val) {
            // if root is null, then return null
            if(!root) return root;
            // if root's val matches val, then return root
            if(root->val == val)
                return root;
            // if root's val is greater than val,
            // so the target node will be in left subtree of root
            if(root->val > val)
                return searchBST(root->left, val);
            // otherwise, it means root's val is less than val,
            // so the target node will be in left subtree of root
            else
                return searchBST(root->right, val);
        }
    };
    ```

-   [x] **Time Complexity :** O(n) where _n_ is the number of nodes in the tree

-   [x] **Space Complexity :** O(n)
