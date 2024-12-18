### Question
Given an array arr[] containing only 0s, 1s, and 2s. Sort the array in ascending order.

### Examples:

1. Input: arr[] = [0, 1, 2, 0, 1, 2]
Output: [0, 0, 1, 1, 2, 2]
Explanation: 0s 1s and 2s are segregated into ascending order.
2. Input: arr[] = [0, 1, 1, 0, 1, 2, 1, 2, 0, 0, 0, 1]
Output: [0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 2, 2]
Explanation: 0s 1s and 2s are segregated into ascending order.

### Solution

```java
/** We can simple sort the array
 **/
```

#### Method 1 - Java
```java
class Solution {
    // time taken : 1.77
    // Function to sort an array of 0s, 1s, and 2s
    public void sort012(int[] arr) {
        // code here
         int low = 0;
        int mid =0;
        int high = arr.length -1;
        int temp = 0;
        
        while(mid <= high){
            if(arr[mid] == 0){
                swap(arr, mid, low);
                mid++;
                low++;
            }
            else if(arr[mid] == 1 ){
                mid++;
            }
            else{
                swap(arr, mid,high);
                high --;
            }
        }
    }
        
        
    static void swap(int arr[], int i, int j){
        int temp = arr[i];
        arr[i] =  arr[j];
        arr[j] = temp;
    }
    
}
```