# Two Sum- Approach and solution  
```solution
🧩 Problem Statement:
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input has exactly one solution, and you may not use the same element twice.

🧠 Approach: Optimized using HashMap
Instead of using two loops (brute force), we use a HashMap to store each number and its index as we iterate.

For each number nums[i]:

Calculate its complement → target - nums[i].

Check if this complement exists in the map.

If yes → we've found the solution → return both indices.

If no → store nums[i] in the map for future reference.

This allows us to find the solution in one pass with O(n) time complexity.

🔍 Time & Space Complexity:
Time Complexity: O(n)

Space Complexity: O(n)
```

### Solution for the problem. (Read Code Comments to understand the flow and logic)  
```Java
// Importing the HashMap and Map classes from java.util package
import java.util.HashMap;
import java.util.Map;

public class Solution {
    
    // Main method to find two indices whose elements sum up to the target
    public int[] twoSum(int[] nums, int target) {

        // Create an empty HashMap to store number as key and its index as value
        Map<Integer, Integer> hashmap = new HashMap<>();

        // Loop through each element in the input array
        for(int i = 0; i < nums.length; i++) {
            
            // Calculate the number needed to reach the target from current element
            int complement = target - nums[i];

            // Check if this complement is already in the map
            if(hashmap.containsKey(complement)) {
                // If found, return the index of complement from map and current index
                // This means nums[hashmap.get(complement)] + nums[i] = target
                return new int[] {hashmap.get(complement), i};
            }

            // If not found, store the current number and its index in the map
            // So we can check it against future elements
            hashmap.put(nums[i], i);
        }

        // If no such pair is found in the entire array, throw an exception
        // (This line will never run if input always guarantees a solution)
        throw new IllegalArgumentException("No two sum solution");
    }
}

```
