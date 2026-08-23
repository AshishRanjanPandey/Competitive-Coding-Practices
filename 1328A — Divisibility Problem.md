# ⚡ Codeforces 1328A — Divisibility Problem

### 📝 Problem Description
You are given two positive integers $a$ and $b$. In one move, you can increase $a$ by $1$ (replace $a$ with $a + 1$). Your task is to find the minimum number of moves you need to perform in order to make $a$ divisible by $b$. It is possible that you have to make $0$ moves, as $a$ may already be divisible by $b$.

**Input:**
- The first line contains one integer $t$ ($1 \le t \le 10^4$) — the number of test cases.
- Each of the following $t$ lines contains two integers $a$ and $b$ ($1 \le a, b \le 10^9$).

**Output:**
- For each test case, print the minimum number of moves required to make $a$ divisible by $b$.

---

### 💡 Key Insights
1. **Mathematical Approach vs. Simulation:**
   - Simulating incrementing $a$ step-by-step ($a \leftarrow a + 1$) will cause a **Time Limit Exceeded (TLE)** error since $a, b \le 10^9$ and $t \le 10^4$.
   - The problem must be resolved in $\mathcal{O}(1)$ time per test case using the modulo operator.
2. **Modulo Arithmetic:**
   - Compute the remainder: $r = a \bmod b$.
   - **Case 1 ($r = 0$):** $a$ is already evenly divisible by $b$. Minimum moves required $= 0$.
   - **Case 2 ($r > 0$):** $a$ exceeds the previous multiple of $b$ by $r$. The next multiple of $b$ is $(b - r)$ units away. Hence, minimum moves required $= b - (a \bmod b)$.
3. **Fast I/O:**
   - Since $t = 10^4$, standard `Scanner` and repeated `System.out.println()` calls introduce significant overhead.
   - Using `BufferedReader`, `StringTokenizer`, and buffering outputs with `StringBuilder` ensures optimal execution speed.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Divisibility Problem (Codeforces 1328A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class DivisibilityProblem {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;
        
        String firstLine = reader.readLine();
        if (firstLine == null) {
            return;
        }
        
        int t = Integer.parseInt(firstLine.trim());
        StringBuilder result = new StringBuilder();
        
        while (t-- > 0) {
            tokenizer = new StringTokenizer(reader.readLine());
            int a = Integer.parseInt(tokenizer.nextToken());
            int b = Integer.parseInt(tokenizer.nextToken());
            
            int remainder = a % b;
            if (remainder == 0) {
                result.append(0).append("\n");
            } else {
                result.append(b - remainder).append("\n");
            }
        }
        
        System.out.print(result);
    }
}
```
### ⏱️ Complexity Analysis

| Metric | Complexity | Description |
| :--- | :--- | :--- |
| **Time Complexity (Per Test Case)** | $\mathcal{O}(1)$ | Basic arithmetic and modulo operation take constant time. |
| **Total Time Complexity** | $\mathcal{O}(t)$ | Processes $t$ independent test cases sequentially ($\approx 10^4$ operations, well within 1.0s). |
| **Auxiliary Space Complexity** | $\mathcal{O}(1)$ | Constant extra space used for variables (`a`, `b`, `remainder`). |
| **Output Space Complexity** | $\mathcal{O}(t)$ | Required by `StringBuilder` to buffer all test case outputs. |
