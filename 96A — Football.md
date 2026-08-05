# 🚀 Codeforces 96A — Football

### 📝 Problem Description
Petya loves football very much. One day, as he was watching a football match, he was writing the players' current positions on a piece of paper. To simplify the situation he depicted it as a string consisting of zeroes and ones. A zero corresponds to players of one team; a one corresponds to players of another team.

If there are at least 7 players of some team standing one after another, then the situation is considered dangerous. You are given the current situation. Determine whether it is dangerous or not.

**Input:**
- The first input line contains a non-empty string consisting of characters `'0'` and `'1'`, representing players. The length of the string does not exceed $100$ characters. There is at least one player from each team present on the field.

**Output:**
- Print `YES` if the situation is dangerous.
- Otherwise, print `NO`.

---

### 💡 Key Insights
1. **Substring Checking:** Since the situation is dangerous when there are 7 or more consecutive identical characters, we only need to check if the string contains either `"0000000"` or `"1111111"`.
2. **Built-in Methods:** In Java, `String.contains()` performs this check efficiently in linear time relative to the length of the string.
3. **Small Constraints:** The maximum string length is only $100$ characters, so a single string inspection executes well within execution limits.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Football (Codeforces 96A)
 * Language: Java 17
 */
public class Football {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String situation = reader.readLine();
        if (situation == null || situation.trim().isEmpty()) {
            return;
        }

        situation = situation.trim();

        // Check if there are 7 consecutive zeroes or seven consecutive ones
        if (situation.contains("0000000") || situation.contains("1111111")) {
            System.out.println("YES");
        } else {
            System.out.println("NO");
        }
    }
}
```
---

### ⏱️ Complexity Analysis

| Type | Complexity | Description |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(N)$ | Where $N$ is the length of the string ($N \le 100$). Checking for target substrings takes linear time relative to $N$. |
| **Space Complexity** | $\mathcal{O}(1)$ | Auxiliary memory is constant beyond storing the input string itself. |

---
