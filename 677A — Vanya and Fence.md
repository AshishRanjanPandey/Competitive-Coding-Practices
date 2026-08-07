# 🚀 Codeforces 677A — Vanya and Fence

### 📝 Problem Description
Vanya and his friends are walking along the fence of height $h$ and they do not want the guard to notice them. In order to achieve this the height of each of the friends should not exceed $h$. If the height of some person is greater than $h$ he can bend down and then he surely won't be noticed by the guard. The height of the $i$-th person is equal to $a_i$.

Consider the width of the person walking as usual to be equal to $1$, while the width of the bent person is equal to $2$. Friends want to talk to each other while walking, so they would like to walk in a single row. What is the minimum width of the road, such that friends can walk in a row and remain unattended by the guard?

**Input:**
- The first line of the input contains two integers $n$ and $h$ ($1 \le n \le 1000$, $1 \le h \le 1000$) — the number of friends and the height of the fence, respectively.
- The second line contains $n$ integers $a_i$ ($1 \le a_i \le 2h$), the $i$-th of them is equal to the height of the $i$-th person.

**Output:**
- Print a single integer — the minimum possible valid width of the road.

---

### 💡 Key Insights
1. **Conditional Width Calculation:** Each person contributes to the total width based on their height relative to the fence height $h$.
2. **Width Decision Rule:**
   - If $a_i > h$, the person must bend down, adding $2$ to the total width.
   - If $a_i \le h$, the person can walk upright, adding $1$ to the total width.
3. **Single Pass:** We can accumulate the answer in a single loop as we read each height, achieving $O(N)$ time complexity.
4. **Fast I/O:** Using `BufferedReader` and `StringTokenizer` ensures minimal overhead when parsing input tokens.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Vanya and Fence (Codeforces 677A)
 * Language: Java 17
 */
public class VanyaAndFence {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String line = reader.readLine();
        if (line == null) {
            return;
        }

        StringTokenizer tokenizer = new StringTokenizer(line);
        int n = Integer.parseInt(tokenizer.nextToken());
        int h = Integer.parseInt(tokenizer.nextToken());

        int totalWidth = 0;
        
        // Read the array of heights from the next line
        tokenizer = new StringTokenizer(reader.readLine());
        for (int i = 0; i < n; i++) {
            int height = Integer.parseInt(tokenizer.nextToken());
            
            // Person must bend down if height > fence height
            if (height > h) {
                totalWidth += 2;
            } else {
                totalWidth += 1;
            }
        }

        // Print the total required road width
        System.out.println(totalWidth);
    }
}
```
### ⚡ Complexity Analysis

| Complexity | Measure | Description |
| :--- | :--- | :--- |
| **Time Complexity** | $O(N)$ | Iterates through the array of $N$ friends once to compute width. |
| **Space Complexity** | $O(1)$ | Uses a fixed amount of extra memory for input variables and total width. |

---
