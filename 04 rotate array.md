### Question
Given an unsorted array arr[]. Rotate the array to the left (counter-clockwise direction) by d steps, where d is a positive integer. Do the mentioned change in the array in place.

Note: Consider the array as circular.

### Examples :
1. Input: arr[] = [1, 2, 3, 4, 5], d = 2
Output: [3, 4, 5, 1, 2]
Explanation: when rotated by 2 elements, it becomes 3 4 5 1 2.
2. Input: arr[] = [2, 4, 6, 8, 10, 12, 14, 16, 18, 20], d = 3
Output: [8, 10, 12, 14, 16, 18, 20, 2, 4, 6]
Explanation: when rotated by 3 elements, it becomes 8 10 12 14 16 18 20 2 4 6.
3. Input: arr[] = [7, 3, 9, 1], d = 9
Output: [3, 9, 1, 7]
Explanation: when we rotate 9 times, we'll get 3 9 1 7 as resultant array.

### Solution
#### Method 1 - Java
```java
// time taken : 0.91
class Solution {
    static void rotateArr(int arr[], int d) {
        int n = arr.length;
        int rot = d > n ? d%n : d;
        int j = 0;
        int temp [] =  new int[n];
        for (int i = rot ; i<n; i++){
            temp[j++] = arr[i];
        }
        while (j < n ){
            for (int i = 0 ; i < rot ;i++){
                temp[j++] =  arr[i];
            }
        }
        
        for(int i = 0 ;  i <  n; i++){
            arr[i] = temp[i];
        }
    }
}
/** Explanation
 * find how much time to rotate, this is important when d > n
 * 1st rotate from rot to n and then from o to rot. 
 * For this we need to push elements into a new temp array to keep track of index of the elem
 **/
```
#### Method 2 - Java
```java
 //time taken : 0.81
class Solution {
    static void rotateArr(int arr[], int d) {
        int n = arr.length;
        int b[] = new int[n];
        // for d = 2 and n =5
        d = d % n; // 2
        for(int i = 0; i<n; i++){
                b[i] = arr[(i+d) % n]; 
                // b[0] = arr[2] 
                // b[1] = arr[3]
                //b[2] = arr[4]
                //b[3] = arr[0]
        }
        for(int i = 0; i<n; i++){
            arr[i] = b[i];
        }
    }
}
/** Explanation:
 * Instead of iterating twice for rotating,we use (i+d)%n of the element to be pushed into the new temp array. 
 * While we have d values calculated and being less than n for each iteration until i+d = n we have elements pushed into b[0], b[1],... like that
 * once i+d = n, from a[0] elements will be pushed into b. 
 **/
```
#### Method 2 - JavaScript
```javascript
 // time taken : 0.56
class Solution {
    rotateArr(arr, d) {
       
        const n = arr.length;
        d = d%n;
        let temp = new Array(n);
        for(let i = 0; i < n; i++){
            temp[i]=arr[(i+d)%n];
        }
        
        for(let i = 0 ; i< n;i++){
            arr[i] =  temp[i];
        }
    }
}
```

#### Method 3 - JavaScript
```javascript
// time taken : 0.6
class Solution {
    rotateArr(arr, d) {
       
        const n = arr.length;
        function reversearr(arr, start, end){
            while(start < end){
                [arr[start], arr[end]] = [arr[end], arr[start]]
                start++;
                end--;
            }
        }
        reversearr(arr, 0, d-1);
        reversearr(arr, d, n-1);
        reversearr(arr, 0, n-1);
    
    }
}
/** Explanation:
 * This use seperate function of swap elements.
 * Then we call this swap/ reverse funtion for different start and end index
 * Note, here it is important to call the function in the order it is called in the solution. i.e, 0 to d-1 => d to n-1 => 0 to n-1
 **/
```

        