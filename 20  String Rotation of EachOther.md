### Question
You are given two strings of equal lengths, s1 and s2. The task is to check if s2 is a rotated version of the string s1.

Note: The characters in the strings are in lowercase.

### Examples :

1. Input: s1 = "abcd", s2 = "cdab"
Output: true
Explanation: After 2 right rotations, s1 will become equal to s2.
2. Input: s1 = "aab", s2 = "aba"
Output: true
Explanation: After 1 left rotation, s1 will become equal to s2.
3. Input: s1 = "abcd", s2 = "acbd"
Output: false
Explanation: Strings are not rotations of each other.

### Solution

#### Method 1 - Java
```java
//Time taken: 0.42 
class Solution {
    // Function to check if two strings are rotations of each other or not.
    public static boolean areRotations(String s1, String s2) {
        // Your code here
        s1 +=s1;
        return s1.lastIndexOf(s2)>=0;
        
    }
}
```
#### Method 2 - JavaScript
```javascript
class Solution {
    areRotations(s1, s2) {
        s1 = s1+s1;
        return s1.includes(s2);
    }
}
```