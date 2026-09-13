# 🚀 Codeforces 723A — The New Year: Meeting Friends

### 📝 Problem Description
There are three friends living on the straight line $Ox$ in Lineland. The first friend lives at the point $x_1$, the second friend lives at the point $x_2$, and the third friend lives at the point $x_3$. They plan to celebrate the New Year together, so they need to meet at one point. 

What is the minimum total distance they have to travel in order to meet at some point and celebrate the New Year? It's guaranteed that the optimal answer is always an integer.

**Input:**
- The first line contains three distinct integers $x_1$, $x_2$, and $x_3$ ($1 \le x_1, x_2, x_3 \le 100$) — the coordinates of the houses of the first, second, and third friends respectively.

**Output:**
- Print one integer — the minimum total distance the friends need to travel in order to meet together.

---

### 💡 Key Insights
1. **Median Minimizes Total Distance:** On a one-dimensional coordinate line, the optimal meeting point that minimizes the sum of absolute deviations $\sum |x_i - p|$ is the **median** coordinate.
2. **Simplified Arithmetic:** Suppose the coordinates are sorted such that $x_{\min} \le x_{\text{mid}} \le x_{\max}$. If the friends meet at $x_{\text{mid}}$:
   - The friend at $x_{\min}$ travels $x_{\text{mid}} - x_{\min}$.
   - The friend at $x_{\text{mid}}$ travels $0$.
   - The friend at $x_{\max}$ travels $x_{\max} - x_{\text{mid}}$.
   
   Summing these yields:
   $$(x_{\text{mid}} - x_{\min}) + 0 + (x_{\max} - x_{\text{mid}}) = x_{\max} - x_{\min}$$
3. **Range of the Points:** The problem reduces directly to finding the spread between the maximum and minimum coordinates: $\max(x_1, x_2, x_3) - \min(x_1, x_2, x_3)$.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;
import java.util.Arrays;

/**
 * Problem: The New Year: Meeting Friends (Codeforces 723A)
 * Language: Java 17
 */
public class MeetingFriends {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String line = reader.readLine();
        if (line == null) {
            return;
        }
        
        StringTokenizer st = new StringTokenizer(line);
        int[] x = new int[3];
        x[0] = Integer.parseInt(st.nextToken());
        x[1] = Integer.parseInt(st.nextToken());
        x[2] = Integer.parseInt(st.nextToken());
        
        // Sorting arranges points in ascending order: [min, median, max]
        Arrays.sort(x);
        
        // Minimum total distance is the span from the smallest to largest point
        int minDistance = x[2] - x[0];
        
        System.out.println(minDistance);
    }
}
```
### 📊 Complexity Analysis

| Type | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(1)$ | Reading 3 inputs, sorting a fixed-size 3-element array, and basic subtraction all execute in constant time. |
| **Space Complexity** | $\mathcal{O}(1)$ | Memory is bounded to a 3-element primitive array and standard I/O buffer pointers, requiring constant auxiliary memory. |
