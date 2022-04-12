---
tags:
    - Recursion
    - Linked List
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/gray-code/](https://leetcode.com/problems/gray-code/){:target="\_blank"}

**Approach 1 : Simple Recursive Approach :slight_smile:**

=== "Java"

    ```java
    class Solution {
        public List<Integer> grayCode(int n) {
            List<Integer> result = new ArrayList<Integer>();

            List<String> codes = generate(n);
            int size = codes.size();

            // Convert the gray codes from binary strings to decimal values
            for(int i = 0; i < size; i++)
                result.add(Integer.parseInt(codes.get(i),2));

            return result;
        }

        public List<String> generate(int n){
            // Base Case
            if(n == 1)
                return Arrays.asList(new String[]{"0", "1"});

            // Recursively get (n-1)bit gray codes
            List<String> codes = generate(n-1);
            List<String> answer = new ArrayList<String>();
            int size = codes.size();

            // Append "0" to (n-1)bit gray codes from first to last
            for(int i = 0; i < size; i++)
                answer.add(new String("0"+codes.get(i)));

            // Append "1" to (n-1)bit gray codes from last to first
            for(int i = size-1; i >= 0; i--)
                answer.add(new String("1"+codes.get(i)));

            // return the n-bit gray codes (binary strings)
            return answer;
        }
    }
    ```

-   [x] **Time Complexity :** O()

-   [x] **Space Complexity :** O(2^n^) where _n_ is number of gray code bits

<hr>
