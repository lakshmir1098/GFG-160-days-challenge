### Question
Given an integer array arr[]. You need to find the maximum sum of a subarray.

### Examples:

1. Input: arr[] = [2, 3, -8, 7, -1, 2, 3]
Output: 11
Explanation: The subarray {7, -1, 2, 3} has the largest sum 11.
2. Input: arr[] = [-2, -4]
Output: -2
Explanation: The subarray {-2} has the largest sum -2.
3. Input: arr[] = [5, 4, 1, 7, 8]
Output: 25
Explanation: The subarray {5, 4, 1, 7, 8} has the largest sum 25.

### Solution

#### Method 1 - Kandane's Algo - Java
```java
class Solution {
    int maxSubarraySum(int[] arr) {
        int n = arr.length;
        int sum = arr[0];
        int max_sum = arr[0];
        
        for ( int i = 1; i<n; i++ ){
            sum =  Math.max(sum+arr[i], arr[i]);
            max_sum =  Math.max(sum, max_sum);
        }
        
        return max_sum ;
    }
}
```

#### Method 2 - Java
```java
class Solution {
    int maxSubarraySum(int[] arr) {
        int n = arr.length;
        int max_so_far = Integer.MIN_VALUE;
        int max_ending_here = 0; 
  
        for (int i = 0; i < n; i++) 
        { 
            max_ending_here = max_ending_here + a[i]; 
            if (max_so_far < max_ending_here) 
                max_so_far = max_ending_here; 
            if (max_ending_here < 0) 
                max_ending_here = 0; 
        } 
        return max_so_far;
    }
}
```