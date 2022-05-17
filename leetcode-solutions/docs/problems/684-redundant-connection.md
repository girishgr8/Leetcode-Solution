---
tags:
    - Depth-First Search
    - Breadth-First Search
    - Union Find
    - Graph
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/redundant-connection/](https://leetcode.com/problems/redundant-connection/){:target="\_blank"}

**Approach 1 : Union-Find Algorithm :smile:**

=== "Java"

    ```java
    class Solution {
        public int[] findRedundantConnection(int[][] edges) {
            int n = edges.length;
            int[] parent = new int[n + 1];
            Arrays.fill(parent, -1);

            for(int i = 0; i < n; i++){
                int u = edges[i][0];
                int v = edges[i][1];

                if(find(parent, u) == find(parent,v))
                    return edges[i];
                union(parent, u, v);
            }

            return null;
        }

        public int find(int[] parent, int node){
            // if the node is parent of itself (we figure this out if we get parent[node] as -1)
            // return the node
            if(parent[node] == -1)
                return node;
            // recursively find the parent of the node
            return find(parent, parent[node]);
        }

        public void union(int[] parent, int u, int v){
            // find parent of node u
            int pU = find(parent, u);

            // find parent of node v
            int pV = find(parent, v);

            // make parent of node 'v' equal to parent of node 'u'
            parent[pV] = pU;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :**

-   [x] **Space Complexity :**
