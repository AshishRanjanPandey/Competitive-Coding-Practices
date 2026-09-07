# ⚡ Codeforces 1352A — Sum of Round Numbers

### 📝 Problem Description
A positive (strictly greater than zero) integer is called round if it is of the form $d00\dots0$. In other words, a positive integer is round if all its digits except the leftmost (most significant) are equal to zero. In particular, all numbers from $1$ to $9$ (inclusive) are round.

For example, the following numbers are round: $4000, 1, 9, 800, 90$. The following numbers are not round: $110, 707, 222, 1001$.

You are given a positive integer $n$ ($1 \le n \le 10^4$). Represent the number $n$ as a sum of round numbers using the minimum number of summands (addends). In other words, you need to represent the given number $n$ as a sum of the least number of terms, each of which is a round number.

**Input:**
- The first line contains an integer $t$ ($1 \le t \le 10^4$) — the number of test cases in the input.
- Then $t$ test cases follow. Each test case consists of a line containing an integer $n$ ($1 \le n \le 10^4$).

**Output:**
- Print $t$ answers to the test cases.
- Each answer must begin with an integer $k$ — the minimum number of summands.
- Next, $k$ space-separated terms must follow, each of which is a round number, and their sum equals $n$. The terms can be printed in any order.

---

### 💡 Key Insights
1. **Positional Place Value Decomposition:**
   - Any positive integer can be uniquely represented in base-10 expanded form:
     $$n = \sum_{i=0}^{m} d_i \cdot 10^i$$
   - Each term $d_i \cdot 10^i$ (where $d_i \in \{1, \dots, 9\}$) has exactly one non-zero digit followed by zeros, which precisely matches the definition of a round number.

2. **Minimality of Summands:**
   - Each non-zero digit contributes to a distinct power of 10. You cannot combine two different base-10 place values into a single round number without introducing multiple non-zero digits (e.g., $9000 + 800 = 9800$, which is not round).
   - Hence, the minimum number of summands $k$ is strictly equal to the count of non-zero digits in $n$.

3. **Algorithm:**
   - Maintain a multiplier tracking the place value, initialized to `multiplier = 1`.
   - In a loop while $n > 0$:
     - Extract the last digit: `digit = n % 10`.
     - If `digit > 0`, store `digit * multiplier` in a collection.
     - Advance the multiplier: `multiplier *= 10`.
     - Strip the last digit: `n /= 10`.
   - Output the size of the collection, followed by the collected values.

4. **Complexity:**
   - **Time Complexity:** $\mathcal{O}(t \cdot \log_{10} n)$ — since $n \le 10^4$, each test case performs at most $5$ iterations. With $t \le 10^4$, total operations are around $5 \times 10^4$, running well under $0.1$ seconds.
   - **Space Complexity:** $\mathcal{O}(1)$ auxiliary space per testcase (excluding the output buffer), storing at most $5$ integers in memory.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.ArrayList;
import java.util.List;

/**
 * Problem: Sum of Round Numbers (Codeforces 1352A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class SumOfRoundNumbers {
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
            List<Integer> roundNumbers = new ArrayList<>();
            int multiplier = 1;

            while (n > 0) {
                int digit = n % 10;
                if (digit > 0) {
                    roundNumbers.add(digit * multiplier);
                }
                multiplier *= 10;
                n /= 10;
            }

            // Output the count of summands
            output.append(roundNumbers.size()).append("\n");

            // Output the round numbers separated by spaces
            for (int i = 0; i < roundNumbers.size(); i++) {
                output.append(roundNumbers.get(i));
                if (i < roundNumbers.size() - 1) {
                    output.append(" ");
                }
            }
            output.append("\n");
        }

        System.out.print(output);
    }
}
```
### ⏱️ Complexity Analysis

| Metric | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(t \cdot \log_{10} n)$ | Each test case processes at most $\lfloor \log_{10} n \rfloor + 1 \le 5$ digits. Total operations across $t = 10^4$ test cases are $\le 5 \times 10^4$, executing in under $0.1\text{ s}$. |
| **Space Complexity** | $\mathcal{O}(1)$ auxiliary | The list stores at most $5$ summands per testcase in memory before flushing via `StringBuilder`. |
