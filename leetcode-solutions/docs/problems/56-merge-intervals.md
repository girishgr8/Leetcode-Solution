---
tags:
    - Array
    - Sorting
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/merge-intervals/](https://leetcode.com/problems/merge-intervals/){:target="\_blank"}

**Approach : Sorting :smile:**

=== "Java"

    ```java
    class Solution {
        public int[][] merge(int[][] intervals) {
            Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
            List<int[]> list = new ArrayList<int[]>();
            int idx = 0;
            list.add(intervals[0]);
            for(int i = 1; i < intervals.length; i++){
                int[] arr = list.get(idx);
                if(arr[1] >= intervals[i][0]){
                    arr[1] = Math.max(arr[1],intervals[i][1]);
                    list.set(idx, arr);
                }else{
                    list.add(intervals[i]);
                    idx++;
                }
            }
            int n = list.size();
            int[][] result = new int[n][2];
            for(int i = 0; i < n; i++)
                result[i] = list.get(i);
            return result;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(nlogn + n + n) where n = given number of intervals

-   [x] **Space Complexity :** O(n) where n = given number of intervals
