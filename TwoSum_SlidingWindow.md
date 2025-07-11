# Two Sum in a Sorted Array

## 🔍 Problem Statement
Given a **sorted array** of integers, find two numbers such that they add up to a specific target.

Return their **1-based indices** as an array.  
Assume there is **exactly one solution**.

### Example
Input: [2, 7, 11, 15], Target = 9  
Output: [1, 2]

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Nested Loops)

#### Logic:
- Use two loops to try every possible pair and check if the sum equals the target.

#### Code:
```java
public class TwoSumBrute {
    public static int[] twoSum(int[] numbers, int target) {
        for (int i = 0; i < numbers.length; i++) {
            for (int j = i + 1; j < numbers.length; j++) {
                if (numbers[i] + numbers[j] == target) {
                    return new int[]{i + 1, j + 1}; // 1-based indexing
                }
            }
        }
        return new int[]{-1, -1}; // if no solution found
    }

    public static void main(String[] args) {
        int[] numbers = {2, 7, 11, 15};
        int[] result = twoSum(numbers, 9);
        System.out.println(result[0] + " " + result[1]);
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N²)
- **Space:** O(1)

---

### 🔹 Approach 2: Optimal - Two Pointers

#### Logic:
- Start with two pointers: one at the start, one at the end.
- If the sum > target → move right pointer left.
- If the sum < target → move left pointer right.
- If sum == target → return the indices.

#### Code:
```java
public class TwoSumOptimal {
    public static int[] twoSum(int[] numbers, int target) {
        int left = 0, right = numbers.length - 1;
        while (left < right) {
            int sum = numbers[left] + numbers[right];
            if (sum == target) {
                return new int[]{left + 1, right + 1}; // 1-based indexing
            } else if (sum < target) {
                left++;
            } else {
                right--;
            }
        }
        return new int[]{-1, -1}; // if no solution found
    }

    public static void main(String[] args) {
        int[] numbers = {2, 7, 11, 15};
        int[] result = twoSum(numbers, 9);
        System.out.println(result[0] + " " + result[1]);
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N)
- **Space:** O(1)

---

## ✅ Final Thoughts
- Brute Force is simple but inefficient.
- Two Pointers approach is **O(N) and most interviewers expect this.**

---

