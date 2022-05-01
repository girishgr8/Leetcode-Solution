---
tags:
    - Tree
    - Depth-First Search
    - Breadth-First Search
    - Binary Tree
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/binary-tree-right-side-view/](https://leetcode.com/problems/binary-tree-right-side-view/){:target="\_blank"}

**Approach : DFS :smile:**

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
        public List<Integer> rightSideView(TreeNode root) {
            List<Integer> result = new ArrayList<Integer>();
            dfs(root, 0, result);
            return result;

        }
        public void dfs(TreeNode root, int currHeight, List<Integer> result){
            if(root == null)
                return;
            if(currHeight > maxHeight){
                result.add(root.val);
                maxHeight = currHeight;
            }

            dfs(root.right, currHeight + 1, result);
            dfs(root.left, currHeight + 1, result);
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n is number of nodes in the tree

-   [x] **Space Complexity :** O(h) where h is height of the tree
