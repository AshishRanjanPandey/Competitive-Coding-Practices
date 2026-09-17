# 🚀 Codeforces 1703A — YES or YES?

### 📝 Problem Description
There is a string $s$ of length $3$, consisting of uppercase and lowercase English letters. Check if it is equal to `"YES"` (without quotes), where each letter can be in any case. For example, `"yES"`, `"Yes"`, and `"yes"` are all allowable.

**Input:**
- The first line of the input contains an integer $t$ ($1 \le t \le 10^3$) — the number of test cases.
- The description of each test consists of one line containing one string $s$ consisting of three characters. Each character of $s$ is either an uppercase or lowercase English letter.

**Output:**
- For each test case, output `"YES"` (without quotes) if $s$ satisfies the condition, and `"NO"` (without quotes) otherwise.
- You can output `"YES"` and `"NO"` in any case (for example, strings `"yES"`, `"yes"`, and `"Yes"` will be recognized as a positive response).

---

### 💡 Key Insights
1. **Case-Insensitive Match:** The string must match `"YES"` regardless of letter casing. In Java, this can be directly verified using `String.equalsIgnoreCase("YES")` or converting the string to lowercase/uppercase using `toLowerCase()` or `toUpperCase()`.
2. **Fixed String Length:** Each string contains exactly $3$ characters, making comparison practically instantaneous.
3. **I/O Efficiency:** With $t \le 10^3$ test cases, using `BufferedReader` along with `StringBuilder` avoids the overhead of repeated `System.out.println()` calls and handles fast I/O efficiently.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: YES or YES? (Codeforces 1703A)
 * Language: Java 17
 */
public class YesOrYes {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String firstLine = reader.readLine();
        if (firstLine == null || firstLine.trim().isEmpty()) {
            return;
        }
        
        int t = Integer.parseInt(firstLine.trim());
        StringBuilder output = new StringBuilder();
        
        for (int i = 0; i < t; i++) {
            String s = reader.readLine().trim();
            
            // Check if the string equals "YES" ignoring character case
            if (s.equalsIgnoreCase("YES")) {
                output.append("YES\n");
            } else {
                output.append("NO\n");
            }
        }
        
        System.out.print(output);
    }
}
```
### 📊 Complexity Analysis

| Type | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(t \cdot \vert{}s\vert{}) = \mathcal{O}(t)$ | Checking equality of a fixed-length string ($\vert{}s\vert{} = 3$) takes constant time $\mathcal{O}(1)$ per testcase, running in $\mathcal{O}(t)$ overall. |
| **Space Complexity** | $\mathcal{O}(t)$ | `StringBuilder` buffers the output lines across all $t$ test cases before flushing to standard output. |
