### Question
Given an array of positive integers arr[], return the second largest element from the array. If the second largest element doesn't exist then return -1.

Note: The second largest element should not be equal to the largest element.

### Examples:

1. Input: arr[] = [12, 35, 1, 10, 34, 1]
Output: 34
Explanation: The largest element of the array is 35 and the second largest element is 34.
2. Input: arr[] = [10, 5, 10]
Output: 5
Explanation: The largest element of the array is 10 and the second largest element is 5.
3. Input: arr[] = [10, 10, 10]
Output: -1
Explanation: The largest element of the array is 10 and the second largest element does not exist.

### Solution 
#### Method 1 - Java
``` java
//Time taken - 1.27
class Solution {
    public int getSecondLargest(int[] arr) {
        // Code Here
        int n = arr.length; 
        Arrays.sort(arr);
        int max = arr[n-1];
        for (int i = n-2 ; i >=0 ; i--){
            if(arr[i] < max){
                return arr[i];
            }
        }
        return -1;
    }
}
/** Explanation :
    1. sort the array
    2. Take the last elem of sorted array as max
    3. Iterate in desc order and find the number less than max
**/

```
#### Method 2 - Java
```java
//Time Taken - 0.95 
class Solution {
    public int getSecondLargest(int[] arr) {
        int n = arr.length;
        int max = Integer.MIN_VALUE;
        int sec_max = Integer.MIN_VALUE;
        
        for( int i =0 ; i<n ;i++){
            if(arr[i] > max){
                sec_max = max; // -inf 12 
                max = arr[i]; // 12 35
            }
            if(arr[i] > sec_max && arr[i] < max && arr[i] != max){
                sec_max = arr[i];
            }
        }
        
        if (sec_max != Integer.MIN_VALUE)
             return sec_max;
        else
            return -1;
    }
}
/** Explanation : 
    1. intialize max and smax to neg value
    2. if a[i] > max => smax = max and max = a[i]
    3. if a[i] > smax && a[i] != max => smax = a[i] 
```
#### Method 2 - JavaScript
```javascript
//time taken 0.35
class Solution {
    getSecondLargest(arr) {
        const {max, smax} = arr.reduce(( acc, el) =>
        {
            if(el > acc.max){
                acc.smax = acc.max;
                acc.max = el;
            }
            else if (acc.smax < el && el != acc.max){
                acc.smax = el;
            }
            return acc;
            
        },{max: -1, smax:-1});
        
          return smax === -1 ? -1 : smax;
    }
}
```
         
