### Question
Given an array arr[] that contains positive and negative integers (may contain 0 as well). Find the maximum product that we can get in a subarray of arr[].

Note: It is guaranteed that the output fits in a 32-bit integer.

### Examples

1. Input: arr[] = [-2, 6, -3, -10, 0, 2]
Output: 180
Explanation: The subarray with maximum product is {6, -3, -10} with product = 6 * (-3) * (-10) = 180.
2. Input: arr[] = [-1, -3, -10, 0, 6]
Output: 30
Explanation: The subarray with maximum product is {-3, -10} with product = (-3) * (-10) = 30.
3. Input: arr[] = [2, 3, 4] 
Output: 24 
Explanation: For an array with all positive elements, the result is product of all elements. 

### Solution
#### Method 1 - Java
```java
//time taken " 0.51"
class Solution {
    // Function to find maximum product subarray
    int maxProduct(int[] arr) {
        int n = arr.length;
        int result = arr[0];
        int max_prod = arr[0];
        int min_prod = arr[0];
        int temp =1;
        
        for ( int i = 1; i<n; i++ ){
           temp = min(arr[i], min_prod*arr[i], max_prod*arr[i]);
           max_prod = max(arr[i], min_prod*arr[i], max_prod*arr[i]);
           
           min_prod = temp; 
           
           result = Math.max(result, max_prod);
        }
        
        return result ;
    }
    
    private static int min (int a,int b,int c){
        return Math.min(a, Math.min(b,c));
    }
    
    private static int max (int a,int b,int c){
        return Math.max(a, Math.max(b,c));
    }
}

/** Explanation:
 * Let's assume that the input array has only positive elements. Then, we can simply iterate from left to right keeping track of the maximum running product ending at any index. The maximum product would be the product ending at the last index. The problem arises when we encounter zero or a negative element.
 * If we encounter zero, then all the subarrays containing this zero will have product = 0, so zero simply resets the product of the subarray.
 * If we encounter a negative number, we need to keep track of the minimum product as well as the maximum product ending at the previous index. This is because when we multiply the minimum product with a negative number, it can give us the maximum product. So, keeping track of minimum product ending at any index is important as it can lead to the maximum product on encountering a negative number.
 **/ 
```
#### Method 2 - Java
```java
//time taken : 0.54
class Solution {
    // Function to find maximum product subarray
    int maxProduct(int[] arr) {
        int n = arr.length;
        int result = Integer.MIN_VALUE;
        int l2r = 1;
        int r2l = 1;
        int temp =1;
        
        for ( int i = 0; i<n; i++ ){
            if (l2r == 0) l2r = 1;
            if (r2l == 0) r2l = 1;
            
            l2r = l2r * arr[i];
            int j = n-i-1;
            r2l = r2l * arr[j];
            
            result = Math.max(result, Math.max(l2r,r2l));
        }
        
        return result;
        
    }
}
/** Explanation:
 * With an above solution, Problem will occur when our array will contain odd no. of negative elements. In that case, we have to reject one negative element so that we can even no. of negative elements and their product can be positive. Now, since subarray should be contiguous so we can't simply reject any one negative element. We have to either reject the first negative element or the last negative element.
 * Now, if we traverse from start then only the last negative element can be rejected and if we traverse from the last then the first negative element can be rejected. So we will traverse from both ends and find the maximum product subarray.
 **/ 
```