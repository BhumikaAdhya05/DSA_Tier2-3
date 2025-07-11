# Check if Two Arrays Have Common Elements

## 🔍 Problem Statement
Given two arrays, check if they have **at least one common element**.  
Return **true** if they do, else return **false**.

### Example
Input: arr1 = [1, 2, 3, 4], arr2 = [5, 6, 7, 3]  
Output: true

Input: arr1 = [1, 2, 3], arr2 = [4, 5, 6]  
Output: false

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Nested Loops)

#### Logic:
- For every element in arr1, scan arr2 to check if it exists.

#### Code:
```java
public class CommonElementsBrute {
    public static boolean hasCommonElement(int[] arr1, int[] arr2) {
        for (int num1 : arr1) {
            for (int num2 : arr2) {
                if (num1 == num2) {
                    return true;
                }
            }
        }
        return false;
    }

    public static void main(String[] args) {
        int[] arr1 = {1, 2, 3, 4};
        int[] arr2 = {5, 6, 7, 3};
        System.out.println(hasCommonElement(arr1, arr2)); // true
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N * M)
- **Space:** O(1)

---

### 🔹 Approach 2: Optimal - HashSet Lookup

#### Logic:
- Add all elements of arr1 to a HashSet.
- Iterate through arr2 and check if any element exists in the HashSet.

#### Code:
```java
import java.util.HashSet;

public class CommonElementsOptimal {
    public static boolean hasCommonElement(int[] arr1, int[] arr2) {
        HashSet<Integer> set = new HashSet<>();
        for (int num : arr1) {
            set.add(num);
        }

        for (int num : arr2) {
            if (set.contains(num)) {
                return true;
            }
        }

        return false;
    }

    public static void main(String[] args) {
        int[] arr1 = {1, 2, 3, 4};
        int[] arr2 = {5, 6, 7, 3};
        System.out.println(hasCommonElement(arr1, arr2)); // true
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N + M)
- **Space:** O(N)

---

## ✅ Final Thoughts
- Brute Force is fine for very small arrays.
- HashSet lookup is **O(N + M)** and is **the optimal approach** for this problem.

---

