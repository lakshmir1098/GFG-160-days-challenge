### Question
You are given an array of integer arr[] where each number represents a vote to a candidate. Return the candidates that have votes greater than one-third of the total votes, If there's not a majority vote, return an empty array. 

Note: The answer should be returned in an increasing format.

### Examples:

1. Input: arr[] = [2, 1, 5, 5, 5, 5, 6, 6, 6, 6, 6]
Output: [5, 6]
Explanation: 5 and 6 occur more n/3 times.
2. Input: arr[] = [1, 2, 3, 4, 5]
Output: []
Explanation: no candidate occur more than n/3 times.

### Solution

#### Method 1 - Java 
```java
// time taken : 1.57
class Solution {
    // Function to find the majority elements in the array
    public List<Integer> findMajority(int[] arr) {
        // Your code goes here.
        HashMap<Integer, Integer> hm = new HashMap<>();
        List<Integer> li = new ArrayList<>();
        int n = arr.length;
        for ( int i =0; i<n ;i++){
            hm.put(arr[i], hm.getOrDefault(arr[i],0)+1);
        }
        for(Map.Entry<Integer,Integer> it : hm.entrySet()){
            if(it.getValue() > n/3){
                li.add(it.getKey());
            }
        }
        return li;
    }
}

/** Explanation:
 * Always question with finding majority involves HashMap. It the same concept of using hashmap to find the count of the occurance of the elements and then chekc with map iteration for the given condition
 **/
```

#### Method 2 - JavaScript
```javascript
class Solution {
    // Function to find the majority elements in the array
    findMajority(arr) {
        // Your code goes here
        const n = arr.length;
        let map = new Map();
        let ar = new Array();
        
        arr.forEach(i => {
            if(map.has(i)){
                map.set(i, map.get(i)+1);
            }
            else {
                map.set(i, 1); 
            }
        });
        
        map.forEach((v,k) =>{
            if (v > n/3){
                ar.push(k);
            }
        });
        
        return ar.sort();
    }
}
```