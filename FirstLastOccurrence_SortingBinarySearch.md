# First and Last Occurrence of Target in Sorted Array

## 🔍 Problem Statement
Given a sorted array and a target, find the **first and last occurrence (index) of the target element.**  
If not present, return [-1, -1].

### Example
Input: arr = [1, 2, 2, 2, 3, 4, 5], target = 2  
Output: [1, 3]

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Linear Search)

#### Logic:
- Loop through the array.
- Record the **first** and **last** occurrence while scanning.

#### Code:
```java
public class FirstLastOccurrenceBrute {
    public static int[] findFirstLast(int[] arr, int target) {
        int first = -1, last = -1;

        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) {
                if (first == -1) first = i;
                last = i;
            }
        }

        return new int[]{first, last};
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 2, 2, 3, 4, 5};
        int[] res = findFirstLast(arr, 2);
        System.out.println("[" + res[0] + ", " + res[1] + "]");
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N)
- **Space:** O(1)

---

### 🔹 Approach 2: Optimal - Binary Search (Two Pass)

#### Logic:
- **First pass:** Find the first occurrence using binary search.
- **Second pass:** Find the last occurrence using binary search.

#### Code:
```java
public class FirstLastOccurrenceOptimal {
    public static int[] findFirstLast(int[] arr, int target) {
        int first = findOccurrence(arr, target, true);
        int last = findOccurrence(arr, target, false);
        return new int[]{first, last};
    }

    private static int findOccurrence(int[] arr, int target, boolean findFirst) {
        int result = -1;
        int left = 0, right = arr.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] == target) {
                result = mid;
                if (findFirst) right = mid - 1; // Go left for first occurrence
                else left = mid + 1;            // Go right for last occurrence
            } else if (arr[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return result;
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 2, 2, 3, 4, 5};
        int[] res = findFirstLast(arr, 2);
        System.out.println("[" + res[0] + ", " + res[1] + "]");
    }
}
```

#### Time & Space Complexity:
- **Time:** O(log N) + O(log N) → O(log N)
- **Space:** O(1)

---

## ✅ Final Thoughts
- Linear Search works but is not scalable.
- **Binary Search Two-Pass Approach is the expected optimal solution.**

---

