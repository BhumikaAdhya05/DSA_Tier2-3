# 2D Matrix Range Sum Query (2D Prefix Sum)

## 🔍 Problem Statement
Given a **2D matrix**, efficiently calculate the sum of all elements inside the rectangle defined by its upper-left and bottom-right coordinates.  
All queries are of the form (r1, c1, r2, c2).

### Example
Matrix:
```
[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]
```

Query: Sum of rectangle from (0,0) to (1,1) → sum of [[1,2],[4,5]] → **12**

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Sum Every Time)

#### Logic:
- For every query, loop through the sub-matrix and sum all elements.

#### Code:
```java
public class MatrixRangeSumBrute {
    public static int rangeSum(int[][] matrix, int r1, int c1, int r2, int c2) {
        int sum = 0;
        for (int i = r1; i <= r2; i++) {
            for (int j = c1; j <= c2; j++) {
                sum += matrix[i][j];
            }
        }
        return sum;
    }

    public static void main(String[] args) {
        int[][] matrix = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
        System.out.println(rangeSum(matrix, 0, 0, 1, 1)); // Output: 12
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N * M) per query
- **Space:** O(1)

---

### 🔹 Approach 2: Optimal - 2D Prefix Sum (Precompute)

#### Logic:
- Precompute a 2D prefix sum array where:
```
prefix[i][j] = sum of all elements in rectangle from (0,0) to (i,j)
```
- Any query (r1, c1, r2, c2) is answered as:  
```
Sum = prefix[r2][c2] - prefix[r1-1][c2] - prefix[r2][c1-1] + prefix[r1-1][c1-1]
```

#### Code:
```java
public class MatrixRangeSumOptimal {
    public static int[][] buildPrefixSum(int[][] matrix) {
        int n = matrix.length;
        int m = matrix[0].length;
        int[][] prefix = new int[n][m];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                prefix[i][j] = matrix[i][j]
                        + (i > 0 ? prefix[i - 1][j] : 0)
                        + (j > 0 ? prefix[i][j - 1] : 0)
                        - (i > 0 && j > 0 ? prefix[i - 1][j - 1] : 0);
            }
        }

        return prefix;
    }

    public static int rangeSum(int[][] prefix, int r1, int c1, int r2, int c2) {
        int total = prefix[r2][c2];
        if (r1 > 0) total -= prefix[r1 - 1][c2];
        if (c1 > 0) total -= prefix[r2][c1 - 1];
        if (r1 > 0 && c1 > 0) total += prefix[r1 - 1][c1 - 1];
        return total;
    }

    public static void main(String[] args) {
        int[][] matrix = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
        int[][] prefix = buildPrefixSum(matrix);

        System.out.println(rangeSum(prefix, 0, 0, 1, 1)); // Output: 12
        System.out.println(rangeSum(prefix, 1, 1, 2, 2)); // Output: 28
    }
}
```

#### Time & Space Complexity:
- **Preprocessing Time:** O(N * M)
- **Query Time:** O(1)
- **Space:** O(N * M)

---

## ✅ Final Thoughts
- Brute Force recalculates each time → inefficient for large matrices and multiple queries.
- **2D Prefix Sum precomputes → each query takes O(1).**

---

