# Range Sum Query (Prefix Sum)

## 🔍 Problem Statement
Given an array of integers and multiple range queries of the form `(L, R)`,  
find the sum of elements from index L to R (**0-based index**).

### Example
Input:
```
arr = [1, 2, 3, 4, 5]
queries = [(1, 3), (0, 4)]
```

Output:
```
9  // (2 + 3 + 4)
15 // (1 + 2 + 3 + 4 + 5)
```

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Recalculate Every Time)

#### Logic:
- For every query, loop through the array and sum elements from L to R.

#### Code:
```java
public class RangeSumQueryBrute {
    public static int rangeSum(int[] arr, int l, int r) {
        int sum = 0;
        for (int i = l; i <= r; i++) {
            sum += arr[i];
        }
        return sum;
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        System.out.println(rangeSum(arr, 1, 3)); // 9
        System.out.println(rangeSum(arr, 0, 4)); // 15
    }
}
```

#### Time & Space Complexity:
- **Time:** O(Q * N) → Q = number of queries
- **Space:** O(1)

---

### 🔹 Approach 2: Optimal - Prefix Sum Array

#### Logic:
- Build a prefix sum array where prefix[i] = sum of arr[0..i].
- Answer each query in **O(1):**  
  Sum from L to R = prefix[R] - prefix[L-1]  
  Special case: if L = 0, answer is prefix[R].

#### Code:
```java
public class RangeSumQueryOptimal {
    public static int[] buildPrefixSum(int[] arr) {
        int[] prefix = new int[arr.length];
        prefix[0] = arr[0];
        for (int i = 1; i < arr.length; i++) {
            prefix[i] = prefix[i - 1] + arr[i];
        }
        return prefix;
    }

    public static int rangeSum(int[] prefix, int l, int r) {
        if (l == 0) return prefix[r];
        return prefix[r] - prefix[l - 1];
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        int[] prefix = buildPrefixSum(arr);

        System.out.println(rangeSum(prefix, 1, 3)); // 9
        System.out.println(rangeSum(prefix, 0, 4)); // 15
    }
}
```

#### Time & Space Complexity:
- **Time to build:** O(N)
- **Time per query:** O(1)
- **Total time for Q queries:** O(N + Q)
- **Space:** O(N) for prefix array

---

## ✅ Final Thoughts
- Brute Force recalculates every time → inefficient for multiple queries.
- **Prefix Sum precomputes and answers each query in O(1).**

---

