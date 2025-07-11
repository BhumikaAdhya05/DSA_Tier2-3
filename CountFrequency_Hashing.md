# Count Frequency of Elements in an Array

## 🔍 Problem Statement
Given an integer array, count how many times each element occurs and print them.

### Example
Input: [1, 2, 2, 1, 3, 4, 2]  

Output:
```
1 -> 2
2 -> 3
3 -> 1
4 -> 1
```

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Nested Loops)

#### Logic:
- For each element, scan the entire array and count occurrences.
- Print each element only the first time you encounter it.

#### Code:
```java
public class CountFrequencyBrute {
    public static void countFrequency(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            boolean alreadyCounted = false;
            for (int j = 0; j < i; j++) {
                if (arr[i] == arr[j]) {
                    alreadyCounted = true;
                    break;
                }
            }

            if (!alreadyCounted) {
                int count = 1;
                for (int j = i + 1; j < arr.length; j++) {
                    if (arr[i] == arr[j]) {
                        count++;
                    }
                }
                System.out.println(arr[i] + " -> " + count);
            }
        }
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 2, 1, 3, 4, 2};
        countFrequency(arr);
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N²)
- **Space:** O(1)

---

### 🔹 Approach 2: Optimal - HashMap Frequency Counter

#### Logic:
- Traverse the array and store the frequency in a HashMap.
- Print the HashMap entries.

#### Code:
```java
import java.util.HashMap;

public class CountFrequencyOptimal {
    public static void countFrequency(int[] arr) {
        HashMap<Integer, Integer> map = new HashMap<>();

        for (int num : arr) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        for (int key : map.keySet()) {
            System.out.println(key + " -> " + map.get(key));
        }
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 2, 1, 3, 4, 2};
        countFrequency(arr);
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N)
- **Space:** O(N)

---

## ✅ Final Thoughts
- Brute Force is inefficient.
- **HashMap frequency count is the standard approach → O(N).**

---

