---
tags:
    - Tree
    - Breadth-First Search
    - Binary Tree
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/even-odd-tree/](https://leetcode.com/problems/even-odd-tree/){:target="\_blank"}

**Approach : Breadth-First Search :smile:**

-   Idea is to perform level-order traversal using BFS

=== "Java"

    ```java
    /**s
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

    class Node{
        TreeNode node;
        int level;
        int flag;

        public Node(TreeNode node, int level, int flag){
            this.node = node;
            this.level = level;
            this.flag = flag;
        }
    }

    class Solution {
        public boolean isEvenOddTree(TreeNode root) {

            Queue<Node> queue = new LinkedList<Node>();
            queue.add(new Node(root, 0, 1));
            Node previous = new Node(null, -1, -1);

            while(!queue.isEmpty()){
                Node current = queue.poll();

                // current node at even-indexed level has even value OR
                // current node at odd-indexed level has odd value THEN
                // return false
                if((current.node.val & 1) != current.flag)
                    return false;

                // if current node's level equals previous node's level
                if(previous.level == current.level){
                    // if current level is odd-indexed level, then
                    // if previous node's value >= current node's value
                    // return false
                    if(current.flag == 1 && previous.node.val >= current.node.val)
                        return false;

                    // if current level is even-indexed level, then
                    // if previous node's value <= current node's value
                    // return false
                    else if(current.flag == 0 && previous.node.val <= current.node.val)
                        return false;
                }

                // update previous to current
                previous = current;

                // push left node of current node in queue if it is not null
                if(current.node.left != null)
                    queue.add(new Node(current.node.left, current.level + 1, 1 - current.flag));

                // push right node of current node in queue if it is not null
                if(current.node.right != null)
                    queue.add(new Node(current.node.right, current.level + 1, 1 - current.flag));
            }

            return true;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in tree

-   [x] **Space Complexity :** O(n) where h = height of tree
