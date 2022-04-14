---
tags:
    - Backtracking
    - Depth-First Search
    - Breadth-First Search
    - Graph
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/all-paths-from-source-to-target/](https://leetcode.com/problems/all-paths-from-source-to-target/){:target="\_blank"}

**Approach : DFS + Backtracking :smile:**

=== "Java"

    ```java
    class Solution {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        public List<List<Integer>> allPathsSourceTarget(int[][] graph) {
            findPaths(0, graph, new ArrayList<Integer>());
            return result;
        }
        public void findPaths(int node, int[][] graph, List<Integer> list){
            // if node vertex is the target vertex, then add the list to result
            // since we have found one of the directed path to target
            // the list maintains the nodes we which are used to reach vertex 'node'
            if(node == graph.length-1){
                list.add(node);
                result.add(new ArrayList<Integer>(list));
                list.remove(new Integer(node));
                return;
            }
            // add the current node to the list
            list.add(node);
            // recursively find path for through adjacent vertices of current node
            for(int i = 0; i < graph[node].length; i++)
                findPaths(graph[node][i], graph, list);
            // remove the node from the path
            list.remove(new Integer(node));
            return;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(E) where _E_ is the number of edges in DAG

-   [x] **Space Complexity :** O(V) where _V_ is the number of vertices in DAG
