### Question
Given an array of integers arr[] representing a permutation, implement the next permutation that rearranges the numbers into the lexicographically next greater permutation. If no such permutation exists, rearrange the numbers into the lowest possible order (i.e., sorted in ascending order). 

Note - A permutation of an array of integers refers to a specific arrangement of its elements in a sequence or linear order.

### Examples:

1. Input: arr = [2, 4, 1, 7, 5, 0]
Output: [2, 4, 5, 0, 1, 7]
Explanation: The next permutation of the given array is {2, 4, 5, 0, 1, 7}.
2. Input: arr = [3, 2, 1]
Output: [1, 2, 3]
Explanation: As arr[] is the last permutation, the next permutation is the lowest one.
3. Input: arr = [3, 4, 2, 5, 1]
Output: [3, 4, 5, 1, 2]
Explanation: The next permutation of the given array is {3, 4, 5, 1, 2}.

### Solution

#### Method 1 - Java
```java
//time take : 0.99
class Solution {
    void nextPermutation(int[] arr) {
        int n = arr.length;
        int pi = -1;
        
        for(int i = n-2 ;  i >= 0 ; i--){
            if(arr[i] < arr[i+1]){
                pi =  i;
                break;
            }
        }
    
        if(pi == -1){
           reverse (arr,0 , n-1); 
           return;
        }
        
        for (int i = n-1 ;i > pi; i-- ){
            if(arr[i] > arr[pi]){
                swap (arr, i, pi);
                break;
            }
           
        }
    
        
        reverse(arr, pi+1, n-1);
    }
    
    private static void reverse(int[] arr,int l,int r){
        while(l< r) {
            swap (arr, l ,r);
            l++;
            r--;
        }
    }
    
    private static void swap (int[] arr,int a,int b){
        int temp  =  arr[a];
        arr[a] =  arr[b];
        arr[b] =  temp;
    }
}

/** Explanation :
 * Idea here is that, right element should be greater than the left of it 
 * So we start checking from n-2 and if find any i < i+1, then we take i as pivot
 * if pivot is the last element means, there is not next larget permutation, so we return the reverse to get the smallest permutation possible.
 * else, again from last we find the greatest element than pivot element and swap them. Mindful that this happens only once, the first time you find the greates element than pivot you swap and break the loop out
 * once this is done we have to revese the element from pivot+1 to n-1 to get the least closet permutation to the given permutation as we are asked to immediate next permutation
 **/
```

#### Method 1 - JavaScript
```javascript
//time taken : 0.6
class Solution {
    nextPermutation(arr) {
        const n =  arr.length;
        let pi = -1
        for( let i = n-2 ; i >= 0 ; i--){
            if(arr[i] < arr[i+1]){
                pi = i;
                break;
            }
        }
        
        if(pi  == -1){
            arr.reverse();
            return;
        }
        
        for ( let i  = n-1; i > pi ; i--){
            if (arr[i] >  arr[pi]){
                [arr[i], arr[pi]] = [arr[pi],arr[i]];
                break;
            }
        }
        
        let l = pi+1;
        let r = n-1;
        
        while(l<r){
            [arr[l], arr[r]] = [arr[r],arr[l]];
            l++;
            r--;
        }
    }
}
```