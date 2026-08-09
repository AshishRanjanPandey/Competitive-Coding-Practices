# 🚀 Codeforces 116A — Tram

### 📝 Problem Description
Linear Kingdom has exactly one tram line. It has $n$ stops, numbered from 1 to $n$ in the order of tram's movement. At the $i$-th stop $a_i$ passengers exit the tram, while $b_i$ passengers enter it. The tram is empty before it arrives at the first stop. Also, when the tram arrives at the last stop, all passengers exit so that it becomes empty.

Your task is to calculate the tram's minimum capacity such that the number of people inside the tram at any time never exceeds this capacity. Note that at each stop all exiting passengers exit before any entering passenger enters the tram.

**Input:**
- The first line contains a single integer $n$ ($2 \le n \le 1000$) — the number of the tram's stops.
- Then $n$ lines follow, each contains two integers $a_i$ and $b_i$ ($0 \le a_i, b_i \le 1000$) — the number of passengers that exit the tram at the $i$-th stop, and the number of passengers that enter the tram at the $i$-th stop.
- Constraints guarantee that $a_1 = 0$, $b_n = 0$, and the total passengers exiting never exceeds the passengers currently inside.

**Output:**
- Print a single integer denoting the minimum possible capacity of the tram ($0$ is allowed).

---

### 💡 Key Insights
1. **Simulation:** Keep a running count of the current number of passengers inside the tram, initialized to `0`.
2. **Order of Events:** At each stop $i$, $a_i$ passengers exit first, then $b_i$ passengers enter. Update current passengers as `currentPassengers = currentPassengers - a_i + b_i`.
3. **Peak Tracking:** The required capacity is the maximum value that `currentPassengers` reaches at any point during the journey. Maintain a `maxCapacity` variable and update it at every stop.
4. **Time & Space Efficiency:** A single pass through the input processes all $n$ stops in $O(n)$ time using $O(1)$ extra memory.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Tram (Codeforces 116A)
 * Language: Java 17
 */
public class Tram {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String line = reader.readLine();
        if (line == null) {
            return;
        }
        
        int n = Integer.parseInt(line.trim());
        
        int currentPassengers = 0;
        int maxCapacity = 0;
        
        for (int i = 0; i < n; i++) {
            StringTokenizer st = new StringTokenizer(reader.readLine());
            int a = Integer.parseInt(st.nextToken()); // Exiting passengers
            int b = Integer.parseInt(st.nextToken()); // Entering passengers
            
            // Exiting passengers leave first, then entering passengers get on
            currentPassengers -= a;
            currentPassengers += b;
            
            // Track the peak capacity required
            if (currentPassengers > maxCapacity) {
                maxCapacity = currentPassengers;
            }
        }
        
        System.out.println(maxCapacity);
    }
}
```
---

### ⏱️ Complexity Analysis

| Metric | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | We iterate through the $n$ stops exactly once, processing each stop in constant $\mathcal{O}(1)$ time. |
| **Space Complexity** | $\mathcal{O}(1)$ | Only a few primitive integer variables (`currentPassengers`, `maxCapacity`) are maintained, requiring constant extra memory. |
