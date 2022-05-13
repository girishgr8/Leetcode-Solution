---
tags:
    - Array
    - Dynamic Programming
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/){:target="\_blank"}

-   Main idea is to buy the stock on the day with minimum price and sell it on the day with maxmium price once we have brought the stock.

**Approach 1 : Brute Force :sweat_smile:**

-   Idea is to try buying on each day and try selling it on every subsequent days, and check which combination gives maximum profit

=== "Java"

    ```java
    class Solution {
        public int maxProfit(int[] prices) {
            int n = prices.length;
            int maxProfit = 0;

            for(int i = 0; i < n - 1; i++){
                for(int j = i + 1; j < n; j++){
                    maxProfit = Math.max(maxProfit, prices[j] - prices[i]);
                }
            }
            return maxProfit;
        }
    }
    ```

-   [x] **Time Complexity :** O(n^2^) where n is length of array `prices`

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : Dynamic Programming - Preprocessing :smile:**

-   By using extra space, for each day `i`, we pre-compute the maximum stock value after `i`^`th`^ day

=== "Java"

    ```java
    class Solution {
        public int maxProfit(int[] prices) {
            int n = prices.length;
            int maxProfit = 0;

            int highest[] = new int[n];
            highest[n-1] = prices[n-1];

            for(int i = n - 2; i >= 0; i--)
                highest[i] = Math.max(prices[i], highest[i + 1]);

            for(int i = 0; i < n; i++)
                maxProfit = Math.max(maxProfit, highest[i] - prices[i]);

            return maxProfit;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where n is length of array `prices`

-   [x] **Space Complexity :** O(n) where n is length of array `prices`

<hr>

**Approach 3 : Best Approach :smile:**

-   Instead of storing the highest price for each day, we can simply check in single pass if the current day's stock price is greater than the highest stock price seen so far, if current one is highest, then we update the highest seen so far to price[i], and calculate the profit for that day.

=== "Java"

    ```java
    class Solution {
        public int maxProfit(int[] prices) {
            int n = prices.length, maxProfit = 0;
            int highest = 0;

            for(int i = n - 1; i >= 0; i--){
                if(prices[i] > highest)
                    highest = prices[i];
                maxProfit = Math.max(maxProfit, highest - prices[i]);
            }
            return maxProfit;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where n is length of array `prices`

-   [x] **Space Complexity :** O(1)
