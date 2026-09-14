# 🚀 Codeforces 1899A — Game with Integers

### 📝 Problem Description
Vanya and Vova are playing a game. Players are given an integer $n$. On their turn, the player can add $1$ to the current integer or subtract $1$. The players take turns; Vanya starts.

If after Vanya's move the integer is divisible by $3$, then he wins. If $10$ moves have passed and Vanya has not won, then Vova wins.

Write a program that, based on the integer $n$, determines who will win if both players play optimally.

**Input:**
- The first line contains the integer $t$ ($1 \le t \le 100$) — the number of test cases.
- The single line of each test case contains the integer $n$ ($1 \le n \le 1000$).

**Output:**
- For each test case, print `"First"` without quotes if Vanya wins, and `"Second"` without quotes if Vova wins.

---

### 💡 Key Insights
1. **Immediate Win for Vanya:** Vanya moves first. If $n \not\equiv 0 \pmod 3$, $n \pmod 3$ can only be $1$ or $2$.
   - If $n \equiv 1 \pmod 3$, Vanya can subtract $1$ so that $(n - 1) \equiv 0 \pmod 3$.
   - If $n \equiv 2 \pmod 3$, Vanya can add $1$ so that $(n + 1) \equiv 0 \pmod 3$.
   In both situations, Vanya wins on his very first move.
2. **Vova's Counter-Strategy:** If $n \equiv 0 \pmod 3$, any move Vanya makes (adding or subtracting $1$) produces a number that is not divisible by $3$ ($n \pm 1 \not\equiv 0 \pmod 3$). On Vova's turn, Vova can simply reverse Vanya's move (subtracting $1$ if Vanya added $1$, or adding $1$ if Vanya subtracted $1$), bringing the number back to a multiple of $3$. As a result, Vanya can never end his turn on a multiple of $3$, and Vova wins after $10$ moves.
3. **Conclusion:** 
   - If $n \pmod 3 \ne 0 \implies$ `"First"`
   - If $n \pmod 3 = 0 \implies$ `"Second"`

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Game with Integers (Codeforces 1899A)
 * Language: Java 17
 */
public class GameWithIntegers {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String line = reader.readLine();
        if (line == null) {
            return;
        }
        
        int t = Integer.parseInt(line.trim());
        StringBuilder sb = new StringBuilder();
        
        for (int i = 0; i < t; i++) {
            line = reader.readLine();
            while (line != null && line.trim().isEmpty()) {
                line = reader.readLine();
            }
            if (line == null) {
                break;
            }
            
            int n = Integer.parseInt(line.trim());
            
            // If n % 3 != 0, Vanya can win in a single move by either adding or subtracting 1.
            // If n % 3 == 0, Vova can mirror every move and prevent Vanya from ever winning.
            if (n % 3 != 0) {
                sb.append("First\n");
            } else {
                sb.append("Second\n");
            }
        }
        
        System.out.print(sb);
    }
}
```
### 📊 Complexity Analysis

| Metric | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity (per test case)** | $\mathcal{O}(1)$ | The game outcome is decided using a single modulo check (`n % 3 != 0`). |
| **Total Time Complexity** | $\mathcal{O}(t)$ | Processes $t$ independent queries directly, taking under a millisecond for $t \le 100$. |
| **Auxiliary Space Complexity** | $\mathcal{O}(1)$ | Only a few primitive integer variables (`t`, `n`) are maintained in memory. |
| **I/O Space Complexity** | $\mathcal{O}(t)$ | A `StringBuilder` accumulates the output lines to flush them all at once. |
