### Question 
Given an array arr[]. Push all the zeros of the given array to the right end of the array while maintaining the order of non-zero elements. Do the mentioned change in the array in place.

### Examples:

1. Input: arr[] = [1, 2, 0, 4, 3, 0, 5, 0]
Output: [1, 2, 4, 3, 5, 0, 0, 0]
Explanation: There are three 0s that are moved to the end.
2. Input: arr[] = [10, 20, 30]
Output: [10, 20, 30]
Explanation: No change in array as there are no 0s.
3. Input: arr[] = [0, 0]
Output: [0, 0]
Explanation: No change in array as there are all 0s.

### Solution
#### Method 1 - Java
```java
//time taken - 1.35
class Solution {
    void pushZerosToEnd(int[] arr) {        
        int n = arr.length;
        int count = 0;
        for (int i =0 ;i < n; i++ ){
            if (arr[i] != 0 ){
                arr[count++] = arr[i];
            }
        }
        
        while (count < n){
            arr[count++] = 0;
        }
    }
}
/** Explanation:
 * if an array elem is not 0 then push into the array and increase the index with counter.
 * for n-counter time fill the array with 0's 
```

#### Method 1 -  JavaScript
```javascript
class Solution {
    pushZerosToEnd(arr) {
        // code here
        //time taken - 0.45
        let n = arr.length;
        let count =0;
        for (let i of arr) {
            if (i !== 0)
                arr[count++] = i;
        }


        while (count < n)
            arr[count++] = 0;
    }
}
```