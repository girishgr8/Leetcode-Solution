---
tags:
    - Array
    - String
    - Backtracking
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/find-unique-binary-string/](https://leetcode.com/problems/find-unique-binary-string/){:target="\_blank"}

**Approach 1 : Backtracking :sweat_smile:**

=== "Java"

    ```java
    class Solution {
        boolean solve = true;
        String answer = "";
        public String findDifferentBinaryString(String[] nums) {
            int n = nums.length;
            int bits = nums[0].length();
            Set<String> strings = Arrays.stream(nums).collect(Collectors.toSet());
            generate(strings, bits, new ArrayList<Integer>());
            return answer;

        }
        public void generate(Set<String> strings, int bits, List<Integer> list){
            if(!solve) return;
            if(bits == 0){
                StringBuilder sb = new StringBuilder();
                for(Integer b : list)  sb.append(b);
                answer = sb.toString();
                if(!strings.contains(answer)) solve = false;
                return;
            }
            if(!solve) return;
            for(int i = 0; i < 2; i++){
                list.add(i);
                generate(strings, bits-1, list);
                list.remove(new Integer(i));
            }
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :**

-   [x] **Space Complexity :**

<hr>

**Approach 2 : Using proof of [Cantor's Diagonal Argument](https://en.wikipedia.org/wiki/Cantor%27s_diagonal_argument) :smile:**

-   To generate missing string, take complement of i^th^ bit from i^th^ string.

-   This trick can be used since the length of array and number of bits in each string are same.

=== "Java"

    ```java
    class Solution {
        public String findDifferentBinaryString(String[] nums) {
            int n = nums.length;
            StringBuilder sb = new StringBuilder();
            for(int i = 0; i < n; i++)
                sb.append(nums[i].charAt(i) == '1' ? '0' : '1');
            return sb.toString();
        }
    }
    ```
