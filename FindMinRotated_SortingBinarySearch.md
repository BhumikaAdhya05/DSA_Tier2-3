# Find Minimum Element in Rotated Sorted Array

## 🔍 Problem Statement
You are given a **sorted array that has been rotated** at some unknown pivot.  
Find the **minimum element** in O(log N) time.

### Example
Input: [4, 5, 6, 7, 0, 1, 2]  
Output: 0

Input: [3, 4, 5, 1, 2]  
Output: 1

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Scan the Array)

#### Logic:
- Iterate through the array and find the minimum element.

#### Code:
```java
public class FindMinRotatedBrute {
    public static int findMin(int[] arr) {
        int min = arr[0];
        for (int num : arr) {
            if (num < min) {
                min = num;
            }
        }
        return min;
    }

    public static void main(String[] args) {
        int[] arr = {4, 5, 6, 7, 0, 1, 2};
        System.out.println(findMin(arr)); // 0
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N)
- **Space:** O(1)

---

### 🔹 Approach 2: Optimal - Binary Search on Rotated Array

#### Logic:
- Modified binary search:
  - If the middle element is greater than the rightmost → pivot is on the right.
  - Otherwise, the pivot is on the left side (including mid).

#### Code:
```java
public class FindMinRotatedOptimal {
    public static int findMin(int[] arr) {
        int left = 0, right = arr.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] > arr[right]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        return arr[left];
    }

    public static void main(String[] args) {
        int[] arr = {4, 5, 6, 7, 0, 1, 2};
        System.out.println(findMin(arr)); // 0
    }
}
```

#### Time & Space Complexity:
- **Time:** O(log N)
- **Space:** O(1)

---

## ✅ Final Thoughts
- Brute Force works but is not optimal.
- **Binary Search efficiently finds the pivot in O(log N) time.**
- Very common in rotated array type questions.

---

