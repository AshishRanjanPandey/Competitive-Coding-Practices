# 🍀 Codeforces 122A — Lucky Division

### 📝 Problem Description
Petya loves lucky numbers. Lucky numbers are positive integers whose decimal representation contains only the lucky digits `4` and `7` (e.g., `47`, `744`, `4`). 

Petya calls a number **almost lucky** if it is evenly divisible by at least one lucky number (including itself, since all lucky numbers are evenly divisible by themselves).

Determine whether a given integer $n$ is almost lucky.

**Input:**
- A single line containing an integer $n$ ($1 \le n \le 1000$) — the number to be checked.

**Output:**
- Print `"YES"` (without quotes) if $n$ is almost lucky; otherwise, print `"NO"` (without quotes).

---

### 💡 Key Insights
1. **Small Constraint:** Since $n \le 1000$, the set of all possible lucky numbers $\le 1000$ is very small (only 14 numbers in total).
2. **Precomputed Lucky Numbers:** The complete list of lucky numbers up to 1000 is:
   - 1-digit: `4`, `7`
   - 2-digit: `44`, `47`, `74`, `77`
   - 3-digit: `444`, `447`, `474`, `477`, `744`, `747`, `774`, `777`
3. **Modulo Check:** Iterate through the precomputed list. If $n \pmod{\text{lucky}} == 0$ for any lucky number, output `"YES"` and terminate early. If no divisor divides $n$ evenly, output `"NO"`.
4. **Time & Space Complexity:** The check runs in $O(1)$ time and uses $O(1)$ auxiliary space.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Lucky Division (Codeforces 122A)
 * Language: Java 17 / 21
 */
public class LuckyDivision {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String line = reader.readLine();
        if (line == null || line.trim().isEmpty()) {
            return;
        }

        int n = Integer.parseInt(line.trim());

        // All lucky numbers <= 1000
        int[] luckyNumbers = {
            4, 7,
            44, 47, 74, 77,
            444, 447, 474, 477, 744, 747, 774, 777
        };

        boolean isAlmostLucky = false;

        for (int lucky : luckyNumbers) {
            if (n % lucky == 0) {
                isAlmostLucky = true;
                break;
            }
        }

        System.out.println(isAlmostLucky ? "YES" : "NO");
    }
}
```
### ⏱️ Complexity Analysis

| Metric | Complexity | Explanation |
| :--- | :---: | :--- |
| **Time Complexity** | $\mathcal{O}(1)$ | We iterate through a constant array of at most 14 precomputed lucky numbers. |
| **Space Complexity** | $\mathcal{O}(1)$ | Fixed auxiliary memory is used for the constant-sized array and primitive variables. |
