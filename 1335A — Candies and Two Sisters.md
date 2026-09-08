# ⚡ Codeforces 1335A — Candies and Two Sisters

### 📝 Problem Description
There are two sisters, Alice and Betty. You have $n$ candies. You want to distribute these $n$ candies between the two sisters in such a way that:
- Alice will get $a$ ($a > 0$) candies;
- Betty will get $b$ ($b > 0$) candies;
- Each sister will get some integer number of candies;
- Alice will get a greater amount of candies than Betty (i.e., $a > b$);
- All the candies will be given to one of the two sisters (i.e., $a + b = n$).

Your task is to calculate the number of ways to distribute exactly $n$ candies between the sisters according to the conditions described above. Candies are indistinguishable.

Formally, find the number of ways to represent $n$ as the sum $n = a + b$, where $a$ and $b$ are positive integers and $a > b$.

**Input:**
- The first line contains an integer $t$ ($1 \le t \le 10^4$) — the number of test cases.
- Then $t$ test cases follow. Each test case consists of a line containing a single integer $n$ ($1 \le n \le 2 \cdot 10^9$).

**Output:**
- For each testcase, print the number of ways to distribute exactly $n$ candies. If there is no valid distribution, print `0`.

---

### 💡 Key Insights
1. **Mathematical Formulation:**
   - We are given two equations/inequalities:
     $$a + b = n \implies a = n - b$$
     $$a > b \implies n - b > b \implies 2b < n \implies b < \frac{n}{2}$$
   - Since both $a$ and $b$ must be strictly positive integers:
     $$1 \le b < \frac{n}{2}$$

2. **Determining the Range of $b$:**
   - Because candies are indistinguishable, each valid integer choice of $b$ uniquely determines $a = n - b$.
   - The smallest permissible value for $b$ is $1$.
   - The largest permissible integer value for $b$ must be strictly less than $\frac{n}{2}$. In integer arithmetic, this maximal upper bound is:
     $$b_{\max} = \left\lfloor \frac{n - 1}{2} \right\rfloor$$
   - Therefore, the number of valid pairs $(a, b)$ is simply $\left\lfloor \frac{n - 1}{2} \right\rfloor$.

3. **Edge Cases:**
   - If $n = 1$ or $n = 2$:
     $$\left\lfloor \frac{1 - 1}{2} \right\rfloor = 0, \quad \left\lfloor \frac{2 - 1}{2} \right\rfloor = 0$$
     This naturally yields $0$ without requiring explicit conditional checks.
   - Large values of $n$ up to $2 \cdot 10^9$ fit inside a standard signed 32-bit integer, and standard integer arithmetic prevents any overflow.

4. **Algorithm:**
   - Read $t$.
   - For each query $n$, output $(n - 1) / 2$ using integer division.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Candies and Two Sisters (Codeforces 1335A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class CandiesAndTwoSisters {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder output = new StringBuilder();

        String line = reader.readLine();
        if (line == null) {
            return;
        }

        int t = Integer.parseInt(line.trim());

        while (t-- > 0) {
            int n = Integer.parseInt(reader.readLine().trim());
            // Formula: floor((n - 1) / 2)
            output.append((n - 1) / 2).append("\n");
        }

        System.out.print(output);
    }
}
```
### ⏱️ Complexity Analysis

| Metric | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity (Per Test Case)** | $\mathcal{O}(1)$ | Requires only a single integer division and subtraction: `(n - 1) / 2`. |
| **Overall Time Complexity** | $\mathcal{O}(t)$ | Processes $t \le 10^4$ test cases sequentially in $\sim 10^4$ operations, executing in $< 0.1\text{ s}$ (well within the $1.0\text{ s}$ limit). |
| **Space Complexity (Auxiliary)** | $\mathcal{O}(1)$ | Uses a fixed set of primitive variables (`t`, `n`) without allocating any dynamic arrays or collections. |
| **Space Complexity (I/O)** | $\mathcal{O}(t)$ | Uses `StringBuilder` to accumulate output strings for fast bulk printing to avoid I/O bottlenecks. |
