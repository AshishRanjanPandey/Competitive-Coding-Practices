# ⚡ Codeforces 479A — Expression

### 📝 Problem Description
Petya studies in a school and he adores Maths. His class has been studying arithmetic expressions. On the last class the teacher wrote three positive integers $a$, $b$, $c$ on the blackboard. The task was to insert signs of operations `+` and `*`, and probably brackets between the numbers so that the value of the resulting expression is as large as possible.

Let's consider an example: assume that the teacher wrote numbers $1$, $2$, and $3$ on the blackboard. Here are some ways of placing signs and brackets:
- $1 + 2 \times 3 = 7$
- $1 \times (2 + 3) = 5$
- $1 \times 2 \times 3 = 6$
- $(1 + 2) \times 3 = 9$

Note that you can insert operation signs only between $a$ and $b$, and between $b$ and $c$, that is, you cannot swap integers. For instance, in the given sample you cannot get the expression $(1 + 3) \times 2$.

Your task is: given $a$, $b$, and $c$, print the maximum value of the expression that you can obtain.

**Input:**
- Three integers $a$, $b$, and $c$, each on a separate line ($1 \le a, b, c \le 10$).

**Output:**
- Print a single integer — the maximum value that you can obtain.

---

### 💡 Key Insights
1. **Exhaustive Evaluation:**
   - Because the order of numbers is fixed ($a, b, c$), and only binary operators `+` and `*` are allowed, there are only six possible valid evaluation structures:
     1. $a + b + c$
     2. $a \times b \times c$
     3. $a + (b \times c)$
     4. $(a \times b) + c$
     5. $(a + b) \times c$
     6. $a \times (b + c)$

2. **Corner Cases ($1$s):**
   - When all numbers are strictly greater than $1$, multiplication produces the largest result ($a \times b \times c$).
   - However, whenever one or more numbers equal $1$, using addition is better than multiplication (since $x \times 1 = x$, whereas $x + 1 > x$). Brackets allow grouping a $1$ with an adjacent number before multiplying by the third number (e.g., $(1 + 2) \times 3 = 9$).

3. **Complexity:**
   - **Time Complexity:** $\mathcal{O}(1)$ — evaluating a fixed set of $6$ expressions requires constant operations, well within the $1.0$-second limit.
   - **Space Complexity:** $\mathcal{O}(1)$ — requires only constant extra memory.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Expression (Codeforces 479A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class Expression {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String line = reader.readLine();
        if (line == null) {
            return;
        }
        
        int a = Integer.parseInt(line.trim());
        int b = Integer.parseInt(reader.readLine().trim());
        int c = Integer.parseInt(reader.readLine().trim());
        
        int ans1 = a + b + c;
        int ans2 = a * b * c;
        int ans3 = a + (b * c);
        int ans4 = (a * b) + c;
        int ans5 = (a + b) * c;
        int ans6 = a * (b + c);
        
        int max = Math.max(ans1, Math.max(ans2, Math.max(ans3, Math.max(ans4, Math.max(ans5, ans6)))));
        
        System.out.println(max);
    }
}
```
| Metric | Complexity | Description |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(1)$ | Computes a fixed number of arithmetic operations ($6$ expressions) and constant comparison steps regardless of input values. |
| **Space Complexity** | $\mathcal{O}(1)$ | Uses a fixed set of primitive integer variables (`a`, `b`, `c`, and expression results) requiring minimal constant auxiliary memory. |
