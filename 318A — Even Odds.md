# 🔢 Codeforces 318A — Even Odds

### 📝 Problem Description
Being a nonconformist, Volodya is displeased with the natural order of numbers. He writes down the first $n$ positive integers in a new sequence:
1. First, all **odd** integers from $1$ to $n$ in ascending order.
2. Then, all **even** integers from $1$ to $n$ in ascending order.

Given $n$ and $k$, find the number that will stand at position index $k$ (1-based).

**Input:**
- A single line containing two integers $n$ and $k$ ($1 \le k \le n \le 10^{12}$).

**Output:**
- Print the number at position $k$ after Volodya's rearrangement.

---

### 💡 Key Insights
1. **Partitioning the Range:** The total count of odd integers in the range $[1, n]$ is:
   $$\text{oddCount} = \left\lceil \frac{n}{2} \right\rceil = \frac{n + 1}{2}$$
2. **Odd Section ($k \le \text{oddCount}$):** If the requested index falls within the first half, the number is the $k$-th odd integer:
   $$\text{Result} = 2k - 1$$
3. **Even Section ($k > \text{oddCount}$):** If the index falls within the second half, the number is the $(k - \text{oddCount})$-th even integer:
   $$\text{Result} = 2 \cdot (k - \text{oddCount})$$
4. **Data Types:** Since $n, k \le 10^{12}$, 32-bit standard integers will overflow. Use 64-bit integers (`long` in Java).
5. **Time & Space Complexity:**
   - **Time Complexity:** $O(1)$ — solved with basic mathematical logic.
   - **Space Complexity:** $O(1)$ — constant memory usage.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Even Odds (Codeforces 318A)
 * Language: Java 17 / 21
 */
public class EvenOdds {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        String line = reader.readLine();
        
        if (line == null || line.trim().isEmpty()) {
            return;
        }

        StringTokenizer tokenizer = new StringTokenizer(line);
        long n = Long.parseLong(tokenizer.nextToken());
        long k = Long.parseLong(tokenizer.nextToken());

        long oddCount = (n + 1) / 2;

        if (k <= oddCount) {
            System.out.println(2 * k - 1);
        } else {
            System.out.println(2 * (k - oddCount));
        }
    }
}
```
### ⏱️ Complexity Analysis

| Type | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $O(1)$ | Direct mathematical calculation with basic arithmetic checks. |
| **Space Complexity** | $O(1)$ | Uses a constant amount of memory for storing input variables. |
