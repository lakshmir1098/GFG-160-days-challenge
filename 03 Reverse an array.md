### Question
You are given an array of integers arr[]. Your task is to reverse the given array.

### Examples:

1. Input: arr = [1, 4, 3, 2, 6, 5]
Output: [5, 6, 2, 3, 4, 1]
Explanation: The elements of the array are 1 4 3 2 6 5. After reversing the array, the first element goes to the last position, the second element goes to the second last position and so on. Hence, the answer is 5 6 2 3 4 1.
2. Input: arr = [4, 5, 2]
Output: [2, 5, 4]
Explanation: The elements of the array are 4 5 2. The reversed array will be 2 5 4.
3. Input: arr = [1]
Output: [1]
Explanation: The array has only single element, hence the reversed array is same as the original.

### Solution
#### Method 1 -  Java
```java
//Time taken : 0.92
class Solution {
    public void reverseArray(int arr[]) {
        int n = arr.length;
        int temp =0;
        
        int left = 0;
        int right = n-1;
        while (left <  right){
            temp = arr[left];
            arr[left] =  arr[right];
            arr[right] = temp;
            
            left ++;
            right --;
        }
    }
}

/** Explanation:
 * take left and right index.
 * Check and iterate while left < right
 * Swap elements on each iteration
 **/
```

#### Method 2  - Java
```java
// time Taken : 0.87
class Solution {
    public void reverseArray(int arr[]) {
        int n = arr.length;
        int temp =0;
        for ( int i = 0 ; i <n/2 ;  i++){
            temp = arr[i];
            arr[i] =  arr[n-1-i];
            arr[n-1-i] = temp;
        }
    }
}
/** Explanation:
 * Here we iterate only half of the array 
 * And swap is made between element in i and n-1-i index
 **/ 
```


#### Method 3 - JavaScript
```javascript
//time take, - 0.3
class Solution {
    reverseArray(arr) {
        arr.reverse();
    }
}