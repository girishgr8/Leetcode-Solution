---
tags:
    - Depth-First Search
    - Breadth-First Search
    - Union Find
    - Graph
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/is-graph-bipartite/](https://leetcode.com/problems/is-graph-bipartite/){:target="\_blank"}

**Approach 1 : DFS :smile:**

=== "Java"

    ```java
    class Solution {
        public boolean isBipartite(int[][] graph) {
            int V = graph.length;
            boolean[] visited = new boolean[V];
            for(int v = 0; v < V; ++v){
                if(!visited[v] && hasOddLengthCycles(graph, visited, v))
                    return false;
            }
            return true;
        }

        public boolean hasOddLengthCycles(int[][] graph, boolean[] visited, int src){
            int V = graph.length;
            int[] colors = new int[V];
            Arrays.fill(colors, -1);

            Queue<Integer> queue = new LinkedList<Integer>();
            queue.add(src);
            colors[src] = 1;

            while(!queue.isEmpty()){
                int u = queue.poll();
                visited[u] = true;
                for(int i = 0; i < graph[u].length; i++){
                    int v = graph[u][i];
                    if(colors[v] == -1){
                        colors[v] = 1 - colors[u];
                        queue.add(v);
                    }
                    else if(colors[v] == colors[u])
                        return true;
                }
            }
            return false;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in the tree

-   [x] **Space Complexity :** O(n) where n = number of nodes in the tree
