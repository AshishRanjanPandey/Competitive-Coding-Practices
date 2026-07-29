# 🚀 Codeforces 266A — Stones on the Table

### 📝 Problem Description
There are $n$ stones on the table in a row, each of them can be red, green, or blue. Count the minimum number of stones to take from the table so that any two neighboring stones have different colors. Stones in a row are considered neighboring if there are no other stones between them.

**Input:**
The first line contains integer $n$ ($1 \le n \le 50$) — the number of stones on the table.
The next line contains string $s$, which represents the colors of the stones ($i$-th character equals `"R"` for red, `"G"` for green, and `"B"` for blue).

**Output:**
Print a single integer — the minimum number of stones to remove.

---

### 💡 Key Insights
1. **Adjacent Comparison:** To guarantee no two neighboring stones have identical colors, every pair of consecutive stones must be distinct.
2. **Greedy Counting:** Whenever two adjacent stones share the same color (e.g., `"RR"` or `"GG"`), you must remove at least one of them. Therefore, the problem reduces to simply counting how many times $s[i] == s[i-1]$.
3. **Linear Scan:** A single loop starting from index $1$ to $n-1$ comparing the current stone with the previous one accurately counts all required removals.
4. **Efficiency:** Since $n \le 50$, a simple single pass takes $\mathcal{O}(n)$ time and $\mathcal{O}(1)$ auxiliary space, well within Codeforces time and memory limits.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Stones on the Table (Codeforces 266A)
 * Language: Java 17
 */
public class StonesOnTheTable {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        int n = sc.nextInt();
        String s = sc.next();
        sc.close();
        
        int removals = 0;
        
        // Count consecutive duplicate colors
        for (int i = 1; i < n; i++) {
            if (s.charAt(i) == s.charAt(i - 1)) {
                removals++;
            }
        }
        
        // Output the result
        System.out.println(removals);
    }
}
```
### ⚡ Complexity Analysis

| Complexity | Bound | Description |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | We perform a single loop iterating through the string of length $n$. |
| **Space Complexity** | $\mathcal{O}(1)$ | Auxiliary space is constant as only a few scalar variables are used. |
