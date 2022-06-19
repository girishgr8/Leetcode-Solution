---
tags:
    - Tree
    - Depth-First Search
    - Breadth-First Search
    - Binary Tree
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/sum-of-nodes-with-even-valued-grandparent/](https://leetcode.com/problems/sum-of-nodes-with-even-valued-grandparent/){:target="\_blank"}

**Approach : Depth First Search (postorder traversal) :smile:**

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
        int sum = 0;
        public int sumEvenGrandparent(TreeNode root) {
            dfs(root, null, null);
            return sum;
        }

        public void dfs(TreeNode node, TreeNode parent, TreeNode grandparent){
            if(node == null)
                return;

            dfs(node.left, node, parent);
            dfs(node.right, node, parent);

            if(grandparent != null){
                int val = grandparent.val;
                if((val & 1) == 0)
                    sum += node.val;
            }
            return;
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
        int sum = 0;
        int sumEvenGrandparent(TreeNode* root) {
            dfs(root, NULL, NULL);
            return sum;
        }

        void dfs(TreeNode* node, TreeNode* parent, TreeNode* grandparent){
            if(!node)
                return;

            dfs(node->left, node, parent);
            dfs(node->right, node, parent);

            if(grandparent){
                int val = grandparent->val;
                if((val & 1) == 0)
                    sum += node->val;
            }
            return;
        }
    };
    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes

-   [x] **Space Complexity :** O(h) where h = height of tree
