# Binary Search in a Sorted Array

## 🔍 Problem Statement
Given a sorted array of integers, find the index of a target element.  
If not found, return -1.

### Example
Input: arr = [1, 3, 5, 7, 9, 11], target = 7  
Output: 3

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Linear Search)

#### Logic:
- Loop through the array and return the index if the target matches.

#### Code:
```java
public class BinarySearchBrute {
    public static int linearSearch(int[] arr, int target) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) {
                return i;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 7, 9, 11};
        System.out.println(linearSearch(arr, 7)); // Output: 3
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N)
- **Space:** O(1)

---

### 🔹 Approach 2: Optimal - Binary Search

#### Logic:
- Repeatedly divide the array in half and check the middle element.

#### Code:
```java
public class BinarySearchOptimal {
    public static int binarySearch(int[] arr, int target) {
        int left = 0, right = arr.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] == target) return mid;
            else if (arr[mid] < target) left = mid + 1;
            else right = mid - 1;
        }

        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 7, 9, 11};
        System.out.println(binarySearch(arr, 7)); // Output: 3
    }
}
```

#### Time & Space Complexity:
- **Time:** O(log N)
- **Space:** O(1)

---

## ✅ Final Thoughts
- Linear Search works but is inefficient on large sorted arrays.
- **Binary Search is O(log N) and the industry-standard approach.**

---

