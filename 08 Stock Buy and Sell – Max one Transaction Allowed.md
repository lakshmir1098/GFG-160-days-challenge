### Question
Given an array prices[] of length n, representing the prices of the stocks on different days. The task is to find the maximum profit possible by buying and selling the stocks on different days when at most one transaction is allowed. Here one transaction means 1 buy + 1 Sell. If it is not possible to make a profit then return 0.

Note: Stock must be bought before being sold.

### Examples:

1. Input: prices[] = [7, 10, 1, 3, 6, 9, 2]
Output: 8
Explanation: You can buy the stock on day 2 at price = 1 and sell it on day 5 at price = 9. Hence, the profit is 8.
2. Input: prices[] = [7, 6, 4, 3, 1]
Output: 0 
Explanation: Here the prices are in decreasing order, hence if we buy any day then we cannot sell it at a greater price. Hence, the answer is 0.
3. Input: prices[] = [1, 3, 6, 9, 11]
Output: 10 
Explanation: Since the array is sorted in increasing order, we can make maximum profit by buying at price[0] and selling at price[n-1].

### Solution
#### Method 1 - Java
```java
//time taken : 0.35
class Solution {
    public int maximumProfit(int prices[]) {
        // Code here
        int n = prices.length;
        int max_profit = Integer.MIN_VALUE;
        int min = prices[0];
       
        for( int i =0 ; i<n; i++){
            min = Math.min(min, prices[i]);
            max_profit =  Math.max(max_profit, prices[i]-min);
        }
        
        return max_profit;
        
    }
    
    /** Explanation:
     * On each iteration try finsing the min value
     * For the min value found, find max difference with other preceding elems to find max_profit
     **/
}
```

#### Method 2 - JavaScript
```javascript
/time taken : TLE
class Solution {
    maximumProfit(prices) {
        const n = prices.length;
        let max_profit = 0;
        
        for( let i = 0 ; i< n-1; i++){
            for ( let j = i+1 ; j< n; j++){
                max_profit =  Math.max(max_profit,  prices[j]- prices[i]);
            }
        }
        
        return max_profit;
    }
    /** Explantion:
     * for each element of i index find the element with max difference from i using  index. Thst the max_profit
     **/
}
```