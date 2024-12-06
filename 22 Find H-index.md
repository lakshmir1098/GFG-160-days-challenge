###  Question
Given an integer array citations[], where citations[i] is the number of citations a researcher received for the ith paper. The task is to find the H-index.

H-Index is the largest value such that the researcher has at least H papers that have been cited at least H times.

### Examples:

1. Input: citations[] = [3, 0, 5, 3, 0]
Output: 3
Explanation: There are at least 3 papers (3, 5, 3) with at least 3 citations.
2. Input: citations[] = [5, 1, 2, 4, 1]
Output: 2
Explanation: There are 3 papers (with citation counts of 5, 2, and 4) that have 2 or more citations. However, the H-Index cannot be 3 because there aren't 3 papers with 3 or more citations.
3. Input: citations[] = [0, 0]
Output: 0

### Solution
#### Method 1 - Java
```java
// time taken : 0.84
class Solution {
    // Function to find hIndex
    public int hIndex(int[] a) {
        // code here
        Arrays.sort(a);
        int n = a.length;

        for( int i = 0 ; i < n ; i++) {
            if (a[i] >= n-i) {
                return n-i;
            }

        }
           

       ```    
        return 0;    
    }
    
    /** Explanation:
     * First, sort the array in ascending order. We use this because we need to compare how many papers have citations greater than or equal to a specific threshold. 
     * looping through the sorted array and check if the number of citations for a paper (i.e., a[i]) is greater than or equal to the number of remaining papers (i.e., n - i)
     * it means that the H-index is n - i.
     **/
}
```