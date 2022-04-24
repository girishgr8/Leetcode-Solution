---
tags:
    - Depth-First Search
    - Breadth-First Search
    - Union Find
    - Graph
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/is-graph-bipartite/](https://leetcode.com/problems/is-graph-bipartite/){:target="\_blank"}

**Approach 1 : BFS :smile:**

=== "Java"

    ```java
    class Solution {
        public boolean isBipartite(int[][] graph) {
            int V = graph.length;
            int[] colors = new int[V];
            Arrays.fill(colors, -1);
            for(int v = 0; v < V; ++v){
                if(colors[v] == -1 && !isValidColoring(graph, colors, v))
                    return false;
            }
            return true;
        }

        public boolean isValidColoring(int[][] graph, int[] colors, int src){
            Queue<Integer> queue = new LinkedList<Integer>();
            queue.add(src);
            colors[src] = 1;

            while(!queue.isEmpty()){
                int u = queue.poll();
                for(int i = 0; i < graph[u].length; i++){
                    int v = graph[u][i];
                    if(colors[v] == -1){
                        colors[v] = 1 - colors[u];
                        queue.add(v);
                    }
                    else if(colors[v] == colors[u])
                        return false;
                }
            }
            return true;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n + e) where n = number of nodes & edges in the graph respectively

-   [x] **Space Complexity :** O(n) where n = number of nodes in the graph
