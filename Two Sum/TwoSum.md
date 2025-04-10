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
import java.util.HashMap;
import java.util.Map;

public class Solution {

    public int[] twoSum(int[] nums, int target) {

        // HashMap to store the number and its index
        Map<Integer, Integer> hashmap = new HashMap<>();

        // Iterate through the array
        for (int i = 0; i < nums.length; i++) {

            // Calculate the complement number
            int complement = target - nums[i];

            // Check if the complement is already in the map
            if (hashmap.containsKey(complement)) {
                // If found, return the index of the complement and the current index
                return new int[] {hashmap.get(complement), i};
            }

            // Otherwise, store the current number with its index
            hashmap.put(nums[i], i);
        }

        // If no solution is found, throw an error (though problem guarantees one)
        throw new IllegalArgumentException("No two sum solution found.");
    }
}
```
