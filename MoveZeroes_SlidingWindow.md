# Move Zeroes to End of Array

## 🔍 Problem Statement
Given an array of integers, move all 0's to the end **while maintaining the relative order of the non-zero elements.**

Do this in-place without making a copy of the array.

### Example
Input: [0, 1, 0, 3, 12]  
Output: [1, 3, 12, 0, 0]

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Use Extra List)

#### Logic:
- Copy all non-zero elements to a temporary list.
- Fill the original array with non-zero elements first.
- Fill the remaining positions with 0.

#### Code:
```java
import java.util.ArrayList;
import java.util.List;

public class MoveZeroesBrute {
    public static void moveZeroes(int[] arr) {
        List<Integer> temp = new ArrayList<>();
        for (int num : arr) {
            if (num != 0) temp.add(num);
        }

        for (int i = 0; i < temp.size(); i++) {
            arr[i] = temp.get(i);
        }

        for (int i = temp.size(); i < arr.length; i++) {
            arr[i] = 0;
        }
    }

    public static void main(String[] args) {
        int[] arr = {0, 1, 0, 3, 12};
        moveZeroes(arr);
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N)
- **Space:** O(N)

---

### 🔹 Approach 2: Optimal - Two Pointers (In-place)

#### Logic:
- Use a pointer `nonZeroIndex` to mark where the next non-zero should go.
- Loop through the array:
  - If element != 0, swap it with the `nonZeroIndex` and move `nonZeroIndex`.

#### Code:
```java
public class MoveZeroesOptimal {
    public static void moveZeroes(int[] arr) {
        int nonZeroIndex = 0;

        for (int i = 0; i < arr.length; i++) {
            if (arr[i] != 0) {
                // Swap elements
                int temp = arr[i];
                arr[i] = arr[nonZeroIndex];
                arr[nonZeroIndex] = temp;
                nonZeroIndex++;
            }
        }
    }

    public static void main(String[] args) {
        int[] arr = {0, 1, 0, 3, 12};
        moveZeroes(arr);
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N)
- **Space:** O(1)

---

## ✅ Final Thoughts
- Brute Force creates a temporary list: easy but inefficient in terms of space.
- **Optimal approach (Two Pointers)** solves it in-place and is **the expected interview solution.**

---

