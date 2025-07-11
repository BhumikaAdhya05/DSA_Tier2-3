# Maximum Sum Subarray of Size K

## 🔍 Problem Statement
Given an array of integers and a number `K`, find the **maximum sum of any contiguous subarray of size K**.

### Example
Input: arr = [2, 1, 5, 1, 3, 2], k = 3  
Output: 9  
Explanation: Maximum sum subarray is [5, 1, 3]

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Check All Subarrays)

#### Logic:
- Loop through all possible subarrays of size K.
- Calculate the sum for each and track the maximum.

#### Code:
```java
public class MaxSumSubarrayBrute {
    public static int maxSum(int[] arr, int k) {
        int maxSum = Integer.MIN_VALUE;

        for (int i = 0; i <= arr.length - k; i++) {
            int sum = 0;
            for (int j = i; j < i + k; j++) {
                sum += arr[j];
            }
            maxSum = Math.max(maxSum, sum);
        }

        return maxSum;
    }

    public static void main(String[] args) {
        int[] arr = {2, 1, 5, 1, 3, 2};
        int k = 3;
        System.out.println(maxSum(arr, k));
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N * K)
- **Space:** O(1)

---

### 🔹 Approach 2: Optimal - Sliding Window

#### Logic:
- Calculate the sum of the first window of size K.
- Slide the window forward by:
  - Subtracting the element that goes out of the window.
  - Adding the element that comes into the window.
- Keep updating the max sum.

#### Code:
```java
public class MaxSumSubarrayOptimal {
    public static int maxSum(int[] arr, int k) {
        int maxSum = 0;
        int windowSum = 0;

        for (int i = 0; i < k; i++) {
            windowSum += arr[i];
        }
        maxSum = windowSum;

        for (int i = k; i < arr.length; i++) {
            windowSum += arr[i] - arr[i - k];
            maxSum = Math.max(maxSum, windowSum);
        }

        return maxSum;
    }

    public static void main(String[] args) {
        int[] arr = {2, 1, 5, 1, 3, 2};
        int k = 3;
        System.out.println(maxSum(arr, k));
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N)
- **Space:** O(1)

---

## ✅ Final Thoughts
- Brute Force approach checks each subarray → inefficient.
- **Sliding Window is the standard approach in interviews → O(N) in time, constant space.**

---

