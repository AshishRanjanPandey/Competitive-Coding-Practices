# ⚡ Codeforces 61A — Ultra-Fast Mathematician

### 📝 Problem Description
Shapur is testing whether anyone can perform calculations faster than him. In his contest, contestants are given two numbers of equal length consisting only of digits `0` and `1`. 

Contestants must generate a new binary number according to a simple rule:
- The $i$-th digit of the output is `1` if and only if the $i$-th digits of the two input numbers differ.
- Otherwise, the $i$-th digit of the output is `0`.

**Input:**
- Two lines, each containing a single binary string of equal length consisting only of characters `'0'` and `'1'`.
- The strings may contain leading zeros.
- The length of each string does not exceed $100$.

**Output:**
- Print a single line containing the resulting binary string. Do not omit leading zeros.

---

### 💡 Key Insights
1. **Bitwise XOR Operation:** The rule defined ("$1$ if digits differ, $0$ if they are the same") is identical to the standard bitwise XOR ($\oplus$) operation.
2. **Constraint Caution (String vs Integer):**
   - The binary strings can be up to $100$ characters long.
   - Standard numeric types in Java (`int` max 31 bits, `long` max 63 bits) will suffer from integer overflow if parsed numerically.
   - `Integer.toBinaryString()` will drop essential leading zeros.
3. **String Processing:** Treat the inputs directly as strings and process them character by character.
4. **Time & Space Complexity:**
   - **Time Complexity:** $O(N)$ where $N \le 100$ is the length of the strings.
   - **Space Complexity:** $O(N)$ to construct the result using `StringBuilder`.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Ultra-Fast Mathematician (Codeforces 61A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class UltraFastMathematician {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String s1 = reader.readLine();
        String s2 = reader.readLine();

        if (s1 == null || s2 == null) {
            return;
        }

        StringBuilder result = new StringBuilder(s1.length());

        for (int i = 0; i < s1.length(); i++) {
            if (s1.charAt(i) != s2.charAt(i)) {
                result.append('1');
            } else {
                result.append('0');
            }
        }

        System.out.println(result.toString());
    }
}
```
### ⏱️ Complexity Analysis

| Metric | Complexity | Description |
| :--- | :--- | :--- |
| **Time Complexity** | $O(N)$ | Iterates through both binary strings of length $N$ exactly once ($N \le 100$). |
| **Space Complexity** | $O(N)$ | Requires $O(N)$ additional memory to store the resulting characters in a `StringBuilder`. |
