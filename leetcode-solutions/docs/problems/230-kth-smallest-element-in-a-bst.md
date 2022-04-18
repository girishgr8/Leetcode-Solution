---
tags:
    - Tree
    - Depth-First Search
    - Binary Search Tree
    - Binary Tree
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/kth-smallest-element-in-a-bst/](https://leetcode.com/problems/kth-smallest-element-in-a-bst/){:target="\_blank"}

**Approach : Recursion :smile:**

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
        int smallest = -1, count = 0;
        public int kthSmallest(TreeNode root, int k) {
            inorder(root, k);
            return smallest;
        }
        public void inorder(TreeNode root, int k){
            if(root == null)
                return;
            inorder(root.left, k);
            count += 1;
            if(count == k){
                smallest = root.val;
                return;
            }
            inorder(root.right, k);
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in BST

-   [x] **Space Complexity :** O(n) where n = number of nodes in BST
