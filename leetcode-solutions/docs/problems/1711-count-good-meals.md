---
tags:
    - Array
    - Hash Table
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/count-good-meals/](https://leetcode.com/problems/count-good-meals/){:target="\_blank"}

**Approach 1 : Brute Force Approach (Time Limit Exceeded) :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        public int countPairs(int[] deliciousness) {
            int n = deliciousness.length;
            int count = 0;

            Set<Integer> powers = new HashSet<Integer>();
            int val = 1;
            for(int i = 0; i <= 21; i++){
                powers.add(val);
                val *= 2;
            }

            for(int i = 0; i < n - 1; i++){
                for(int j = i + 1; j < n; j++){
                    int sum = deliciousness[i] + deliciousness[j];
                    if(powers.contains(sum)){
                        count++;
                        count %= 1000000007;
                    }
                }
            }
            return count;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(22\*n^2^) where n = length of array `deliciousness`

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : HashMap Approach :smile:**

=== "Java"

    ```java
    class Solution {
        public int countPairs(int[] deliciousness) {
            int n = deliciousness.length;
            int count = 0;
            Map<Integer, Integer> map = new HashMap<Integer, Integer>();
            
            for(int k = 0; k < n; k++){
                int val = 1;
                int num = deliciousness[k];
                for(int i = 0; i <= 21; i++){
                    if(val >= num && map.containsKey(val-num)){
                        count += map.get(val-num);
                        count %= 1000000007;
                    }
                    val *= 2;
                }
                map.put(num, map.getOrDefault(num, 0) + 1);
            }
            return count;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(22\*n) where n = length of array `deliciousness`

-   [x] **Space Complexity :** O(n) where n = length of array `deliciousness`