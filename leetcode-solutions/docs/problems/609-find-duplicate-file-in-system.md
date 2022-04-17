---
tags:
    - Array
    - Hash Table
    - String
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/find-duplicate-file-in-system/](https://leetcode.com/problems/find-duplicate-file-in-system/){:target="\_blank"}

**Approach : HashMap :smile:**

=== "Java"

    ```java
    class Solution {
        public List<List<String>> findDuplicate(String[] paths) {
            Map<String, List<String>> map = new HashMap<String, List<String>>();
            for(int i = 0; i < paths.length; i++){
                String[] arr = paths[i].split(" ");
                String dir = arr[0];
                for(int j = 1; j < arr.length; j++){
                    int idx = arr[j].indexOf("(");
                    String filename = arr[j].substring(0, idx);
                    String content = arr[j].substring(idx + 1, arr[j].indexOf(")"));
                    List<String> list =  map.getOrDefault(content, new ArrayList<String>());
                    String path = dir + "/" + filename;
                    list.add(path);
                    map.put(content, list);
                }
            }
            List<List<String>> result = new ArrayList<List<String>>();
            for(List<String> path : map.values()){
                if(path.size() > 1)
                    result.add(path);
            }
            return result;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(p\*k\*m\*l\*l) where p = paths.length, k = paths[i].length, m = #files in directory, l = len(filename+content)

-   [x] **Space Complexity :**
