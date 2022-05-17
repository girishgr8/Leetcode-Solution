---
tags:
    - Array
    - Hash Table
    - Prefix Sum
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/intervals-between-identical-elements/](https://leetcode.com/problems/intervals-between-identical-elements/){:target="\_blank"}

**Approach 1 : Naive Approach (Time Limit Exceeded) :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        public long[] getDistances(int[] arr) {
            int n = arr.length;
            long[] intervals = new long[n];
            for(int i = 0; i < n; i++){
                long sum = 0;
                for(int j = 0; j < n; j++){
                    if(arr[i] == arr[j])
                        sum += Math.abs(j - i);
                }
                intervals[i] = sum;
            }
            return intervals;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n^2^) where n = length of array `arr`

-   [x] **Space Complexity :** O(1), here we don't consider the space required to return the output

<hr>

**Approach 2 : HashMap + Prefix Sum :smile:**

=== "Java"

    ```java
    class Pair{
        long s;
        int c;
        public Pair(long s, int c){
            this.s = s;
            this.c = c;
        }
    }
    class Solution {
        public long[] getDistances(int[] arr) {
            int n = arr.length;
            List<long[]> before = new ArrayList<long[]>();
            List<long[]> after = new ArrayList<long[]>();
            long[] intervals = new long[n];
            HashMap<Integer, Pair> map = new HashMap<Integer, Pair>();
            for(int i = 0; i < n; i++){
                if(map.containsKey(arr[i])){
                    Pair p = map.get(arr[i]);
                    before.add(new long[]{p.c, p.s});
                    p.c++;
                    p.s += i;
                    map.put(arr[i], p);
                }
                else{
                    before.add(new long[]{0, 0});
                    map.put(arr[i], new Pair((long)i, 1));
                }
            }
            map.clear();
            for(int i = n - 1; i >= 0; i--){
                if(map.containsKey(arr[i])){
                    Pair p = map.get(arr[i]);
                    after.add(new long[]{p.c, p.s});
                    p.c++;
                    p.s += i;
                    map.put(arr[i], p);
                }
                else{
                    after.add(new long[]{0, 0});
                    map.put(arr[i], new Pair((long)i, 1));
                }
            }
            for(int i = 0; j = n - 1 - i; i < n; i++, j--){
                long beforeSum = Math.abs(before.get(i)[1] - before.get(i)[0] * i);
                long afterSum = Math.abs(after.get(n-1-i)[1] - after.get(n-1-i)[0] * i);
                intervals[i] = Math.abs(beforeSum + afterSum);
            }

            return intervals;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = length of array `arr`

-   [x] **Space Complexity :** O(n) where n = length of array `arr`
