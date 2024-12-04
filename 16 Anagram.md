### Question
Given two strings s1 and s2 consisting of lowercase characters. The task is to check whether two given strings are an anagram of each other or not. An anagram of a string is another string that contains the same characters, only the order of characters can be different. For example, act and tac are an anagram of each other. Strings s1 and s2 can only contain lowercase alphabets.

Note: You can assume both the strings s1 & s2 are non-empty.

### Examples :

1. Input: s1 = "geeks", s2 = "kseeg"
Output: true
Explanation: Both the string have same characters with same frequency. So, they are anagrams.
2. Input: s1 = "allergy", s2 = "allergic"
Output: false
Explanation: Characters in both the strings are not same, so they are not anagrams.
3. Input: s1 = "g", s2 = "g"
Output: true
Explanation: Character in both the strings are same, so they are anagrams.

### Solution

#### Method 1 - Java
```java
//time taken -  0.51
class Solution {
    // Function is to check whether two strings are anagram of each other or not.
    public static boolean areAnagrams(String s1, String s2) {

        // Your code here
        HashMap<Character, Integer> map = new HashMap<>();
        for(char ch : s1.toCharArray()){
            map.put(ch, map.getOrDefault(ch, 0 )+ 1);
        }
        
        for(char ch : s2.toCharArray()){
            map.put(ch, map.getOrDefault(ch, 0) -1);
        }
        
        for(var e : map.entrySet()){
            if(e.getValue()  != 0){
                return false;
            }
        }
        
        return true;
    }
}
```

#### Method 2 - JavaScript
```javascript
class Solution {
    areAnagrams(s1, s2) {
        let chcounts = {}; // this is also Map in JS

        for (let ch of s1) {
            if (chcounts[ch]) {
                chcounts[ch] += 1;
            } else {
                chcounts[ch] = 1;
            }
        }
        
        for (let ch of s2) {
            if (chcounts[ch]) {
                chcounts[ch] -= 1;
            } else {
                chcounts[ch] = 1;
            }
        }
        
        
        /**
         * Method 2 of using Map in JS for strings
            let chcounts = {};
            for (let ch of s1) 
                charCount[ch] = (charCount[ch] || 0) + 1;

            for (let ch of s2) 
                charCount[ch] = (charCount[ch] || 0) - 1;
        
        **/
        
        /** Method 3 of unsing Map in JS
             let chcounts = new Map();
            
            for (let ch of s1) {
                if (chcounts.has(ch)) {
                    chcounts.set(ch, chcounts.get(ch) + 1);
                } else {
                    chcounts.set(ch, 1);
                }
            }
            
            for (let [key, value] of chcounts) {
                console.log(`Key: ${key}, Value: ${value}`);
            } 
        **/
        
        for( let key in chcounts){
            if(chcounts[key] !== 0 ){
                return false;
            }
        }
        return true;
        
    }
}
```
