---
tags:
    - Depth-First Search
    - Breadth-First Search
    - Union Find
    - Graph
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/number-of-provinces/](https://leetcode.com/problems/number-of-provinces/){:target="\_blank"}

-   This problem basically asks us to find _number of connected components_.
-   To find number of connected components, we can either use
    -   Depth-First Search + Stack
    -   Breadth-First Search + Queue
    -   Union-Find Algorithm

**Approach : Depth-First Search :smile:**

=== "Java"

    ```java
    class Solution {
        boolean[] visited;
        public int findCircleNum(int[][] isConnected) {
            int n = isConnected.length, provinces = 0;
            // visited[i] = true means i-th city is already visited & part of some province
            visited = new boolean[n];
            for(int i = 0; i < n; i++){
                if(!visited[i]){
                    DFS(i, isConnected);
                    provinces++;
                }
            }
            return provinces;
        }

        public void DFS(int u, int[][] isConnected){
            // we are at some unvisited city 'u' of some province
            // visit this city 'u'
            visited[u] = true;

            // recursively visit its connected cities
            for(int v = 0; v < isConnected[u].length; v++){
                if(isConnected[u][v] != 0 && !visited[v])
                    // recursively perform DFS on the connected city 'v' of city 'u'
                    DFS(v, isConnected);
            }
            return;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n^2^) where n = number of cities

-   [x] **Space Complexity :** O(n) where n = number of cities
