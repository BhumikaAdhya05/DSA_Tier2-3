# First Non-Repeating Character in a String

## 🔍 Problem Statement
Given a string, find the **first non-repeating character** and return its index. If it doesn't exist, return -1.

### Example
Input: "leetcode"  
Output: 0  

Input: "aabb"  
Output: -1

---

## 🛠️ Approaches

---

### 🔹 Approach 1: Brute Force (Nested Loops)

#### Logic:
- For each character, scan the entire string to check if it repeats.
- Return the index of the first character that has no duplicates.

#### Code:
```java
public class FirstNonRepeatingBrute {
    public static int firstUniqChar(String s) {
        for (int i = 0; i < s.length(); i++) {
            boolean isUnique = true;
            for (int j = 0; j < s.length(); j++) {
                if (i != j && s.charAt(i) == s.charAt(j)) {
                    isUnique = false;
                    break;
                }
            }
            if (isUnique) return i;
        }
        return -1;
    }

    public static void main(String[] args) {
        System.out.println(firstUniqChar("leetcode")); // 0
        System.out.println(firstUniqChar("aabb")); // -1
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N²)
- **Space:** O(1)

---

### 🔹 Approach 2: Optimal - HashMap Frequency Count

#### Logic:
- Traverse the string and store the frequency of each character using a HashMap.
- Traverse the string again to find the first character whose frequency is 1.

#### Code:
```java
import java.util.HashMap;

public class FirstNonRepeatingOptimal {
    public static int firstUniqChar(String s) {
        HashMap<Character, Integer> map = new HashMap<>();

        // Count frequency
        for (char c : s.toCharArray()) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }

        // Find first non-repeating
        for (int i = 0; i < s.length(); i++) {
            if (map.get(s.charAt(i)) == 1) {
                return i;
            }
        }

        return -1;
    }

    public static void main(String[] args) {
        System.out.println(firstUniqChar("leetcode")); // 0
        System.out.println(firstUniqChar("aabb")); // -1
    }
}
```

#### Time & Space Complexity:
- **Time:** O(N)
- **Space:** O(26) → constant, because it's just lowercase letters.

---

## ✅ Final Thoughts
- Brute Force works but is slow (O(N²)).
- HashMap is **O(N) optimal** and most interviewers will expect this approach.

---

