### Question
You are given an integer array arr[]. Your task is to find the smallest positive number missing from the array.

Note: Positive number starts from 1. The array can have negative integers too.

### Examples:

1. Input: arr[] = [2, -3, 4, 1, 1, 7]
Output: 3
Explanation: Smallest positive missing number is 3.
2. Input: arr[] = [5, 3, 2, 5, 1]
Output: 4
Explanation: Smallest positive missing number is 4.
3. Input: arr[] = [-8, 0, -1, -4, -3]
Output: 1
Explanation: Smallest positive missing number is 1.

### Solution

#### Method 1 - Java
```java
// time taken : 0.87
class Solution {
    public int missingNumber(int[] arr) {
        // Your code here
        int n = arr.length;
        Arrays.sort(arr);
        int chek = 1;
        
        for ( int i = 0 ; i < n ;i++){
            if (arr[i] == chek){
                chek++;
            }
           else if (arr[i] > chek) {
                break;
            }
        }
        return chek;
    }
}
/** Explanation:
 * Sort the array
 * create an counter and then compare with counter
 * if a[i] == count -> count++
 * if a[i] > count, mean we passed the missing element and so we print count
 **/
```
####  Method 2 - Java
```java
// Using visiting array
// time taken : 0.59
class Solution {
    public int missingNumber(int[] arr) {
        // Your code here
        int n = arr.length;
        boolean[] vis = new boolean[n];
        for ( int i = 0 ; i < n ;i++){
            if(arr[i] >=1 && arr[i] <= n){
                vis[arr[i]-1] = true; // since we consider from no.1 and index is from 0 we are using arr[i]-1
            }
        }
        
        for ( int i = 0 ; i < n ;i++){
            if(!vis[i]){
                return i+1;
           }
       }
       
       return n+1;
    }
}
/** Explanation:
 * we are creating a boolean array of n length where intially all elements are false by default
 * Then we are making the vis elem true only if the current arr array has i+1 index as their element.
 * the first false element (consider, i+1 index) in vis array is the smallest missing number 
 * If all elements are true then n+1 is the smallest missing number.
 **/
```

#### Method 3 - Java
```java
// using cyle sort 
// cycle sort can be used only on positive natural numbers i.e 1,2,....,n where n is length of an array.
// The basic idea behind cycle sort is to divide the input array into cycles, where each cycle consists of elements that belong to the same position in the sorted output array. The algorithm then performs a series of swaps to place each element in its correct position within its cycle, until all cycles are complete and the array is sorted.
// time taken : 0.62
class Solution {
    public int missingNumber(int[] arr) {
        // Your code here
        int n = arr.length;
        
        for ( int i = 0 ; i < n ;i++){
            while(arr[i] >=1 && arr[i] <= n &&
              arr[i] != arr[arr[i] - 1]){
                int temp = arr[i];
                arr[i] = arr[arr[i] - 1];
                arr[temp - 1] = temp;
            }
        }
        
        for ( int i = 1 ; i <= n ;i++){
             if (i != arr[i - 1]) {
                return i;
            }
       }
       
       return n+1;
    }
}
