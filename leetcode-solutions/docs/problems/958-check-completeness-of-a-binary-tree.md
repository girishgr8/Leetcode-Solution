---
tags:
    - Tree
    - Breadth-First Search
    - Binary Tree
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/check-completeness-of-a-binary-tree/](https://leetcode.com/problems/check-completeness-of-a-binary-tree/){:target="\_blank"}

**Approach : Breadth-First Search :smile:**

-   Once we find a null node in the queue, no non-null node should appear in the queue

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
        public boolean isCompleteTree(TreeNode root) {
            Queue<TreeNode> queue = new LinkedList<TreeNode>();
            queue.add(root);
            TreeNode previous = root;

            while(!queue.isEmpty()){
                TreeNode current = queue.poll();

                if(previous == null && current != null)
                    return false;

                if(current != null){
                    queue.add(current.left);
                    queue.add(current.right);
                }

                previous = current;
            }
            return true;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in the binary tree

-   [x] **Space Complexity :** O(n) where n = number of nodes in the binary tree
