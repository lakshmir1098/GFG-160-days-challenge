### Question
The cost of stock on each day is given in an array price[]. Each day you may decide to either buy or sell the stock at price[i], you can even buy and sell the stock on the same day. Find the maximum profit that you can get.

Note: A stock can only be sold if it has been bought previously and multiple stocks cannot be held on any given day.

### Examples:

1. Input: prices[] = [100, 180, 260, 310, 40, 535, 695]
Output: 865
Explanation: Buy the stock on day 0 and sell it on day 3 => 310 – 100 = 210. Buy the stock on day 4 and sell it on day 6 => 695 – 40 = 655. Maximum Profit = 210 + 655 = 865.

2. Input: prices[] = [4, 2, 2, 2, 4]
Output: 2
Explanation: Buy the stock on day 3 and sell it on day 4 => 4 – 2 = 2. Maximum Profit = 2.


### Solution

#### Method 1 - Java
```java
//time taken: 0.24
class Solution { 
    public int maximumProfit(int prices[]) {
        int lmin = prices[0];
        int lmax =  prices[0];
        int i = 0;
        int n = prices.length;
        int profit = 0;
        
        while(i < n-1){
            if( i < n-1 && prices[i] >= prices[i + 1]){
                i++;
            }
            lmin = prices[i];
            
            if(  i < n-1 && prices[i] <= prices[i+1]){
                i++;
            }
            lmax = prices[i];
            
            profit  += (lmax - lmin);
        }
        
       return profit;
    }
    
    /** Explanation:
     * THis aprrocah involves finding max and min for entire array.
     * min => arr[i] < arr[i+1] so until then we have to i++   => so that why we have prices[i] >=  prices[i+1] {i++}
     * max => arr[i] > arr[i+1] so until then we have to i++   => so that why we have prices[i] <=  prices[i+1] {i++}
     * Then again since we can have multiple buy and sell, we sum each time we encounter min and max range within 0 to n-1 lenght of the array
     **/
}
```

#### Method 2 - JavaScript 
```javascript
//time taken : 0.09
class Solution {
    maximumProfit(prices) {
        
        let profit = 0;

    
        for (let i = 1; i < prices.length; i++) {
            if (prices[i] > prices[i - 1]) 
                profit += prices[i] - prices[i - 1];
                // 80 + 80 + 50 + 495 + 160 =  865
        }
    
        return profit;
    }
    
    /** Explanation:
     * This is hte simplified form of the previous method
     * Idea here is, add the difference of current and previous elem only if previous elem is less than current
     * 
     * arr[i] > arr[i -1] => profit += (arr[i]  - arr[i-1])
     **/
}
```