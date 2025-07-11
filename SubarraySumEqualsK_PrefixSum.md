# Subarray Sum Equals K

## 🔍 Problem Statement
Given an integer array `nums` and an integer `k`,  
find the **total number of continuous subarrays whose sum equals to `k`.**

### Example
Input: nums = [1, 1, 1], k = 2  
Output: 2  
Explanation: [1, 1] occurs twice.

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Check All Subarrays)

#### Logic:
- Try every possible subarray and calculate its sum.
- Increment the count if the sum equals `k`.

#### Code:
```java
public class SubarraySumEqualsKBrute {
    public static int subarraySum(int[] nums, int k) {
        int count = 0;

        for (int start = 0; start < nums.length; start++) {
            int sum = 0;
            for (int end = start; end < nums.length; end++) {
                sum += nums[end];
                if (sum == k) {
                    count++;
                }
            }
        }

        return count;
    }

    public static void main(String[] args) {
        int[] nums = {1, 1, 1};
        System.out.println(subarraySum(nums, 2)); // Output: 2
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N²)
- **Space:** O(1)

---

### 🔹 Approach 2: Optimal - Prefix Sum + HashMap

#### Logic:
- Maintain a running prefix sum.
- Use a **HashMap to store frequency of each prefix sum.**
- For each element:
  - Calculate current prefix sum.
  - If (prefix sum - k) exists in the map → increment count by its frequency.
  - Add the current prefix sum to the map.

#### Code:
```java
import java.util.HashMap;

public class SubarraySumEqualsKOptimal {
    public static int subarraySum(int[] nums, int k) {
        HashMap<Integer, Integer> prefixSumCount = new HashMap<>();
        prefixSumCount.put(0, 1); // Initialize for subarrays starting at index 0

        int sum = 0, count = 0;

        for (int num : nums) {
            sum += num;

            if (prefixSumCount.containsKey(sum - k)) {
                count += prefixSumCount.get(sum - k);
            }

            prefixSumCount.put(sum, prefixSumCount.getOrDefault(sum, 0) + 1);
        }

        return count;
    }

    public static void main(String[] args) {
        int[] nums = {1, 1, 1};
        System.out.println(subarraySum(nums, 2)); // Output: 2
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N)
- **Space:** O(N) for HashMap

---

## ✅ Final Thoughts
- Brute Force approach works but is inefficient for large arrays.
- **Prefix Sum + HashMap is the optimal approach → O(N) time.**
- This is one of the most important Prefix Sum interview questions.

---

