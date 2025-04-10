# 📘 Problem Statement: LeetCode #242 – Valid Anagram  
Given two strings s and t, return true if t is an anagram of s, and false otherwise.  
An anagram is a word formed by rearranging all the letters of another word, using each letter exactly once.  
Your task is to check if t is a rearrangement of s, using all characters exactly once.  
💡 That’s it — it has nothing to do with real words or checking against a dictionay.  

```java
Input: s = "anagram", t = "nagaram"
Output: true

Input: s = "rat", t = "car"
Output: false
```
## ❌ Brute Force Approach  
💡 Logic:  
Sort both strings and compare them.  
If the sorted strings are equal, they are anagrams.  

🕒 Time Complexity: O(n log n)  
💾 Space Complexity: O(1) (or O(n) depending on sorting implementation)  

```java
import java.util.Arrays;

public class Solution {
    public boolean isAnagram(String s, String t) {
        // If lengths are not equal, they can't be anagrams
        if (s.length() != t.length()) {
            return false;
        }

        // Convert both strings to character arrays and sort them
        char[] sArr = s.toCharArray();
        char[] tArr = t.toCharArray();

        Arrays.sort(sArr);  // Sort first string
        Arrays.sort(tArr);  // Sort second string

        // Compare sorted arrays
        return Arrays.equals(sArr, tArr);
    }
}
```
🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹

## ✅ Optimal Approach: Using Character Frequency Count  
💡 Logic:  
If lengths of s and t are not equal → not an anagram.  
Count frequency of each character in s.  
Subtract the frequency based on characters in t.  
If any frequency goes negative or character doesn't exist → not an anagram.  

🕒 Time Complexity: O(n)  
💾 Space Complexity: O(1) (only lowercase English letters)  

```java
public class Solution {
    public boolean isAnagram(String s, String t) {

        // Step 1: If the lengths are not equal, they can't be anagrams
        if (s.length() != t.length()) {
            return false;
        }

        // Step 2: Create an integer array of size 26 to count character frequencies
        // Only lowercase English letters are used (a-z)
        int[] count = new int[26];

        // Step 3: Count the frequency of each character in string s
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);          // Get character from s
            count[ch - 'a']++;              // Increment count at respective index
        }

        // Step 4: Subtract frequency based on string t
        for (int i = 0; i < t.length(); i++) {
            char ch = t.charAt(i);          // Get character from t
            count[ch - 'a']--;              // Decrement count

            // If count becomes negative, character is extra in t or more than in s
            if (count[ch - 'a'] < 0) {
                return false;
            }
        }

        // Step 5: All character counts are balanced, return true
        return true;
    }

    // Optional: Test method
    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.isAnagram("anagram", "nagaram")); // true
        System.out.println(sol.isAnagram("rat", "car"));         // false
    }
}
```

Approach🔹 🔹 🔹 🔹Time Complexity🔹 🔹 🔹 🔹Space Complexity🔹 🔹 🔹 🔹	Notes  
Brute Force 🔹 🔹O(n log n)🔹 🔹O(n)🔹 🔹Uses sorting  
Optimal (Map)	🔹 🔹O(n)🔹 🔹	O(1)🔹 🔹	Uses character frequency array  
