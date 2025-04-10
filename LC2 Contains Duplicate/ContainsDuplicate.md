# Contains Duplicate  

## 🧾 Problem Statement  
Given an integer array nums, return true if any value appears at least twice, and false if every element is distinct.  

```java
Input:  nums = [1, 2, 3, 1]
Output: true
Explanation: 1 appears more than once

Input:  nums = [1, 2, 3, 4]
Output: false
Explanation: All elements are unique
```
## Approach:  
### Brute Force Approach:  
Compare each element with every other using two nested loops.  

🕒 Time Complexity: O(n^2)  
💾 Space Complexity: O(1)  
### Brute force code:  
```java
public class Solution {

    // Method to check if array contains any duplicate elements
    public boolean containsDuplicate(int[] nums) {

        // Outer loop - iterate through each element in the array
        for (int i = 0; i < nums.length; i++) {

            // Inner loop - compare the current element with all elements after it
            for (int j = i + 1; j < nums.length; j++) {

                // Check if the two elements are equal (duplicate found)
                if (nums[i] == nums[j]) {
                    return true;  // Return true immediately if a duplicate is found
                }
            }
        }

        // If the entire array is traversed without finding duplicates, return false
        return false;
    }

    // Optional main method to test the function
    public static void main(String[] args) {
        Solution sol = new Solution();

        int[] nums1 = {1, 2, 3, 1};  // Contains duplicate
        int[] nums2 = {1, 2, 3, 4};  // No duplicates

        System.out.println(sol.containsDuplicate(nums1));  // Output: true
        System.out.println(sol.containsDuplicate(nums2));  // Output: false
    }
}
```
#### 🔍 Logic Summary:  
We use two nested loops:  
The outer loop picks one element.  
The inner loop checks if the same value appears later.  
If a match is found → return true.  
If the loop finishes without matches → return false.  
#### ⚠️ Drawback:  
Time Complexity: O(n^2) → Slow for large arrays.  
Works fine for small input sizes or for learning purposes.  
🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹 🔹  

### Optimal Approach: Using a Set  
🧠 Idea:  
Loop through the array once.  
For each number:  
If it's already in a set → duplicate found → return True  
Otherwise, add it to the set  
If loop ends without finding duplicates → return False  
🕒 Time Complexity: O(n)  
💾 Space Complexity: O(n)  

```java
import java.util.HashSet;
import java.util.Set;

public class Solution {

    // Method to check if the array contains any duplicate values
    public boolean containsDuplicate(int[] nums) {

        // Create a HashSet to store unique elements seen so far
        // A Set automatically prevents duplicate entries
        Set<Integer> seen = new HashSet<>();

        // Loop through each number in the input array
        for (int num : nums) {

            // Check if the current number already exists in the set
            if (seen.contains(num)) {
                // If yes, it means we've seen this number before => duplicate found
                return true;
            }

            // If not in the set, add the number to the set for future checks
            seen.add(num);
        }

        // If the loop completes without finding duplicates, return false
        return false;
    }

    // Main method to test the containsDuplicate() function
    public static void main(String[] args) {

        Solution sol = new Solution();

        // Test case 1: has a duplicate (1)
        int[] nums1 = {1, 2, 3, 1};
        System.out.println(sol.containsDuplicate(nums1)); // Output: true

        // Test case 2: no duplicates
        int[] nums2 = {1, 2, 3, 4};
        System.out.println(sol.containsDuplicate(nums2)); // Output: false

        // Test case 3: all elements are duplicates
        int[] nums3 = {5, 5, 5, 5};
        System.out.println(sol.containsDuplicate(nums3)); // Output: true
    }
}
```
#### 💡 Summary of What’s Happening:  
✅ Uses a HashSet for fast lookup (O(1) average time).  
✅ Iterates the array only once (O(n) time).  
✅ Adds each new element to the set if it’s not already present.  
✅ Returns true on the first duplicate found, making it efficient.  
