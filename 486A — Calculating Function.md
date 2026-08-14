# 🚀 Codeforces 486A — Calculating Function

### 📝 Problem Description
For a positive integer $n$ let's define a function $f$:
$$f(n) = -1 + 2 - 3 + \dots + (-1)^n n$$

Your task is to calculate $f(n)$ for a given integer $n$.

**Input:**
- The single line contains a positive integer $n$ ($1 \le n \le 10^{15}$).

**Output:**
- Print $f(n)$ in a single line.

---

### 💡 Key Insights
1. **Pairwise Cancellation Pattern:** Iterating from $1$ to $n$ will result in a Time Limit Exceeded (TLE) error since $n \le 10^{15}$. Instead, observe how terms group in consecutive pairs:
   $$(-1 + 2) + (-3 + 4) + (-5 + 6) + \dots$$
   Each pair $(-k + (k + 1))$ simplifies to $+1$.
2. **Even vs. Odd Cases:**
   - **If $n$ is even:** There are exactly $\frac{n}{2}$ pairs, so the total sum is simply $\frac{n}{2}$.
   - **If $n$ is odd:** Group the first $n - 1$ terms into $\frac{n - 1}{2}$ pairs (which sum to $\frac{n - 1}{2}$) and add the final isolated term $-n$:
     $$f(n) = \frac{n - 1}{2} - n = -\frac{n + 1}{2}$$
3. **Data Type & Complexity:** Because $n$ can be up to $10^{15}$, store values in a 64-bit integer (`long` in Java) to avoid integer overflow. The closed-form formula executes in $O(1)$ time and uses $O(1)$ auxiliary space.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Calculating Function (Codeforces 486A)
 * Language: Java 17
 */
public class CalculatingFunction {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String input = reader.readLine();
        if (input == null || input.trim().isEmpty()) {
            return;
        }
        
        long n = Long.parseLong(input.trim());
        
        if (n % 2 == 0) {
            System.out.println(n / 2);
        } else {
            System.out.println(-(n + 1) / 2);
        }
    }
}
```
### ⏱️ Complexity Analysis

| Complexity | Measure | Description |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(1)$ | Closed-form formula computed via a single arithmetic operation in constant time. |
| **Space Complexity** | $\mathcal{O}(1)$ | Uses a single `long` variable without additional heap or dynamic memory allocations. |

---
