# Reverse an Array

## 🔍 Problem Statement
Given an array of integers, reverse its elements in-place without using extra space (for the optimal approach).

### Example
Input: [1, 2, 3, 4, 5]  
Output: [5, 4, 3, 2, 1]

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Extra Array)

#### Logic:
- Create a new array of the same size.
- Copy the elements from the original array in reverse order.
- Return the new array.

#### Code:
```java
public class ReverseArrayBrute {
    public static int[] reverse(int[] arr) {
        int[] reversed = new int[arr.length];
        for (int i = 0; i < arr.length; i++) {
            reversed[i] = arr[arr.length - 1 - i];
        }
        return reversed;
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        int[] result = reverse(arr);
        for (int num : result) {
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
- Initialize two pointers: left at 0, right at n - 1.
- Swap elements at left and right.
- Move left++ and right-- until left >= right.

#### Code:
```java
public class ReverseArrayOptimal {
    public static void reverse(int[] arr) {
        int left = 0, right = arr.length - 1;
        while (left < right) {
            int temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;
            left++;
            right--;
        }
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        reverse(arr);
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
- Brute Force uses extra space → not preferred in interviews.
- **Two Pointers approach is the best → in-place & optimal.**
