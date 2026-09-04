# ⚡ Codeforces 510A — Fox And Snake

### 📝 Problem Description
Fox Ciel starts to learn programming. The first task is drawing a fox! However, that turns out to be too hard for a beginner, so she decides to draw a snake instead.

A snake is a pattern on an $n \times m$ table. Denote the $c$-th cell of the $r$-th row as $(r, c)$. The tail of the snake is located at $(1, 1)$, then its body extends to $(1, m)$, then goes down $2$ rows to $(3, m)$, then goes left to $(3, 1)$ and so on.

Your task is to draw this snake for Fox Ciel: the empty cells should be represented as dot characters (`'.'`) and the snake cells should be filled with number signs (`'#'`).

**Input:**
- The only line contains two integers: $n$ and $m$ ($3 \le n, m \le 50$).
- $n$ is guaranteed to be an odd number.

**Output:**
- Output $n$ lines. Each line should contain a string consisting of $m$ characters without spaces.

---

### 💡 Key Insights
1. **Row Parity Breakdown:**
   - **Odd rows** ($r = 1, 3, 5, \dots$): Represent horizontal segments of the snake. Every cell across the entire row is filled with `'#'`.
   - **Even rows** ($r = 2, 4, 6, \dots$): Represent the vertical turns connecting the horizontal segments. Exactly one cell contains `'#'`, while the remaining $m - 1$ cells contain `'.'`.

2. **Alternating Turn Direction:**
   - The vertical turn rows alternate sides every cycle:
     - When $r \equiv 2 \pmod 4$ (i.e., $r = 2, 6, 10, \dots$): The turn is on the far **right** side. The pattern is `....#`.
     - When $r \equiv 0 \pmod 4$ (i.e., $r = 4, 8, 12, \dots$): The turn is on the far **left** side. The pattern is `#....`.

3. **Buffering Output:**
   - Instead of printing character-by-character, assembling rows or building the full grid inside a `StringBuilder` ensures minimal overhead and clean output.

4. **Complexity:**
   - **Time Complexity:** $\mathcal{O}(n \cdot m)$ — Every cell in the $n \times m$ grid is visited and printed exactly once. With $n, m \le 50$, the total number of operations is bounded by $2\,500$, well within the 2.0-second time limit.
   - **Space Complexity:** $\mathcal{O}(n \cdot m)$ — Space utilized by the output buffer `StringBuilder`.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Fox And Snake (Codeforces 510A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class FoxAndSnake {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        String line = reader.readLine();
        if (line == null || line.trim().isEmpty()) {
            return;
        }

        StringTokenizer tokenizer = new StringTokenizer(line);
        int n = Integer.parseInt(tokenizer.nextToken());
        int m = Integer.parseInt(tokenizer.nextToken());

        StringBuilder sb = new StringBuilder();

        for (int r = 1; r <= n; r++) {
            if (r % 2 != 0) {
                // Odd rows are completely filled with '#'
                for (int c = 0; c < m; c++) {
                    sb.append('#');
                }
            } else {
                // Even rows alternate between having '#' at the right or left end
                if (r % 4 == 2) {
                    // Turn right: m - 1 dots followed by '#'
                    for (int c = 0; c < m - 1; c++) {
                        sb.append('.');
                    }
                    sb.append('#');
                } else {
                    // Turn left: '#' followed by m - 1 dots
                    sb.append('#');
                    for (int c = 0; c < m - 1; c++) {
                        sb.append('.');
                    }
                }
            }
            sb.append('\n');
        }

        System.out.print(sb);
    }
}
```
### 📊 Complexity Analysis

| Metric | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n \cdot m)$ | Visits each cell in the $n \times m$ grid once. For $n, m \le 50$, total operations $\le 2\,500$ (runs in $< 0.1\text{ s}$). |
| **Auxiliary Space** | $\mathcal{O}(n \cdot m)$ | Space consumed by `StringBuilder` to buffer all $n \times m$ characters before printing. |
| **Input Parsing** | $\mathcal{O}(1)$ | Only two integers ($n, m$) are parsed from standard input. |
