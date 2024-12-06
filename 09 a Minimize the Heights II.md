### Question
Given an array arr[] denoting heights of N towers and a positive integer K.

For each tower, you must perform exactly one of the following operations exactly once.

Increase the height of the tower by K
Decrease the height of the tower by K
Find out the minimum possible difference between the height of the shortest and tallest towers after you have modified each tower.

You can find a slight modification of the problem here.
Note: It is compulsory to increase or decrease the height by K for each tower. After the operation, the resultant array should not contain any negative integers.

### Examples :

1. Input: k = 2, arr[] = {1, 5, 8, 10}
Output: 5
Explanation: The array can be modified as {1+k, 5-k, 8-k, 10-k} = {3, 3, 6, 8}.The difference between the largest and the smallest is 8-3 = 5.
2. Input: k = 3, arr[] = {3, 9, 12, 16, 20}
Output: 11
Explanation: The array can be modified as {3+k, 9+k, 12-k, 16-k, 20-k} -> {6, 12, 9, 13, 17}.The difference between the largest and the smallest is 17-6 = 11. 

### Solution
 #### Method 1 - Java
 ```java
 //tine taken : 0.69
class Solution {
    int getMinDiff(int[] arr, int k) {
        // code here
       int n = arr.length;
        Arrays.sort(arr);
        int diff = arr[n - 1] - arr[0];
        for (int i = 0; i < n-1; i++) {
            int l = Math.max(arr[n-1]-k, arr[i]+k);
            int s = Math.min (arr[0]+k, arr[i+1]-k);
            
            if(l < 0 || s < 0 ) continue;
            
            diff = Math.min(diff, l-s);
        }
        
        
        return diff;  
    }
    
    /** Explanation
     * Sort the arrya and fins the difference between 1st and last elem. This should be the min diff for now without k involved.
     * take the smallest as arr[0] + k and largest as arr[n-1] - k
     * For smallest of all, compare  arr[0]+k, with all arr[i+1]-k
     * For largest of all, compare arr[n-1]-k with all arr[i]+k
     * Then check if the largest and smallest are positive as -ve are not allowed.
     * Then find the min of diff between the each iteration of large and small found.
     **/
 }
 ```
 