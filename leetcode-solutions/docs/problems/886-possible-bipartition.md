---
tags:
    - Depth-First Search
    - Breadth-First Search
    - Union Find
    - Graph
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/possible-bipartition/](https://leetcode.com/problems/possible-bipartition/){:target="\_blank"}

**Approach : Breadth-First Search Approach :smile:**

=== "Java"

    ```java
    class Solution {
        public boolean possibleBipartition(int n, int[][] dislikes) {
            if(dislikes.length == 0)
                return true;

            int[] colors = new int[n + 1];
            List<List<Integer>> list = new ArrayList<List<Integer>>();

            Arrays.fill(colors, -1);
            for(int i = 0; i <= n; i++)
                list.add(new ArrayList<Integer>());

            for(int i = 0; i < dislikes.length; i++){
                int u = dislikes[i][0];
                int v = dislikes[i][1];
                list.get(u).add(v);
                list.get(v).add(u);
            }
            for(int i = 1; i <= n; i++){
                if(colors[i] == -1 && !isTwoColorable(i, list, colors))
                    return false;
            }
            return true;
        }

        public boolean isTwoColorable(int src, List<List<Integer>> list, int[] colors){
            Queue<Integer> queue = new LinkedList<Integer>();
            queue.add(src);
            colors[src] = 1;
            while(!queue.isEmpty()){
                int u = queue.poll();
                int n = list.get(u).size();
                for(int i = 0; i < n; i++){
                    int v = list.get(u).get(i);
                    if(colors[v] == -1){
                        colors[v] = ~colors[u];
                        queue.add(v);
                    }
                    else if(colors[u] == colors[v])
                        return false;
                }
            }
            return true;
        }
    }
    ```

=== "C++"

    ```c++
    ```

-   [x] **Time Complexity :** O(n) where n is the number of people

-   [x] **Space Complexity :** O(n) where n is the number of people
