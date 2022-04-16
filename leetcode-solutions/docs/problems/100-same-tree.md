---
tags:
    - Tree
    - Depth-First Search
    - Breadth-First Search
    - Binary Tree
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/same-tree/](https://leetcode.com/problems/same-tree/){:target="\_blank"}

**Approach 1 : Recursive Approach :smile:**

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
        public boolean isSameTree(TreeNode p, TreeNode q) {
            if(p == null && q == null)
                return true;
            if(p == null || q == null)
                return false;
            if(p.val != q.val)
                return false;
            return (isSameTree(p.left, q.left) && isSameTree(p.right, q.right));
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in tree

-   [x] **Space Complexity :** O(h) where h = height of tree

<hr>

**Approach 2 : Iterative Approach :sweat_smile:**

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
        public boolean isSameTree(TreeNode p, TreeNode q) {
            Queue<TreeNode> queue = new LinkedList<>();
            if(p == null && q == null)
                return true;
            else if(p == null || q == null)
                return false;
            if (p != null && q != null) {
                queue.add(p);
                queue.add(q);
            }
            while (!queue.isEmpty()) {
                TreeNode first = queue.poll();
                TreeNode second = queue.poll();
                if (first == null && second == null)
                    continue;
                if (first == null || second == null)
                    return false;
                if (first.val != second.val)
                    return false;
                queue.add(first.left);
                queue.add(second.left);
                queue.add(first.right);
                queue.add(second.right);
            }
            return true;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in tree

-   [x] **Space Complexity :** O(h) where h = height of tree
