# Search Insert Position

## 🔍 Problem Statement
Given a sorted array and a target, return the index if the target is found.  
If not, return the index **where it would be inserted** in order.

### Example
Input: arr = [1, 3, 5, 6], target = 5 → Output: 2  
Input: arr = [1, 3, 5, 6], target = 2 → Output: 1  

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Linear Search)

#### Logic:
- Traverse the array.
- Return the first index where the element is greater than or equal to the target.

#### Code:
```java
public class SearchInsertBrute {
    public static int searchInsert(int[] arr, int target) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] >= target) {
                return i;
            }
        }
        return arr.length; // Insert at the end
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 6};
        System.out.println(searchInsert(arr, 5)); // 2
        System.out.println(searchInsert(arr, 2)); // 1
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N)
- **Space:** O(1)

---

### 🔹 Approach 2: Optimal - Binary Search

#### Logic:
- Standard binary search.
- If the target is not found, return the **left pointer**, which points to the correct insert position.

#### Code:
```java
public class SearchInsertOptimal {
    public static int searchInsert(int[] arr, int target) {
        int left = 0, right = arr.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] == target) return mid;
            else if (arr[mid] < target) left = mid + 1;
            else right = mid - 1;
        }

        return left; // Insertion point
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 6};
        System.out.println(searchInsert(arr, 5)); // 2
        System.out.println(searchInsert(arr, 2)); // 1
    }
}
```

#### Time & Space Complexity:
- **Time:** O(log N)
- **Space:** O(1)

---

## ✅ Final Thoughts
- Linear Search is fine for small arrays.
- **Binary Search is the optimal way to find insertion position in O(log N) time.**

---

