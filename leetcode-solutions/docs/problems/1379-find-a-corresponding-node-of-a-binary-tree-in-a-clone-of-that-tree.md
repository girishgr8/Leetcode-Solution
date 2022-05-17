---
tags:
    - Tree
    - Depth-First Search
    - Breadth-First Search
    - Binary Tree
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/](https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/){:target="\_blank"}

**Approach 1 : Depth-First Search :smile:**

-   While performing preorder traversal check if the current node's value matches the target node's value

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
        public final TreeNode getTargetCopy(final TreeNode original, final TreeNode cloned, final TreeNode target) {
            if(original == null)
                return null;

            if(original.val == target.val)
                return cloned;

            final TreeNode left = getTargetCopy(original.left, cloned.left, target);
            final TreeNode right = getTargetCopy(original.right, cloned.right, target);

            if(left == null)
                return right;
            else
                return left;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in the tree

-   [x] **Space Complexity :** O(h) where h = height of tree

<hr>

**Approach 2 : Breadth-First Search :smile:**

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
        public final TreeNode getTargetCopy(final TreeNode original, final TreeNode cloned, final TreeNode target) {
            Queue<TreeNode> queue = new LinkedList<TreeNode>();

            // push root node of original tree & cloned tree at the start
            queue.add(original);
            queue.add(cloned);

            while(!queue.isEmpty()){
                // remove two nodes from queue
                // first one is node of original tree
                // other one is node of cloned tree
                TreeNode ogNode = queue.poll();
                TreeNode clNode = queue.poll();

                // if value of original node removed from queue matches value of target node
                // return the polled cloned tree node
                if(ogNode.val == target.val)
                    return clNode;

                // if the left child of original tree is not null
                // push the left child of current node of both original tree & cloned tree
                if(ogNode.left != null){
                    queue.add(ogNode.left);
                    queue.add(clNode.left);
                }

                // if the right child of original tree is not null
                // push the right child of current node of both original tree & cloned tree
                if(ogNode.right != null){
                    queue.add(ogNode.right);
                    queue.add(clNode.right);
                }
            }

            return null;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in the tree

-   [x] **Space Complexity :** O(n) where n = number of nodes in the tree
