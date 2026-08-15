# 🧲 Codeforces 344A — Magnets

### 📝 Problem Description
Mad scientist Mike entertains himself by arranging rows of rectangular magnets. Each magnet has two poles: positive (`"01"`, plus-minus) or negative (`"10"`, minus-plus). 

When placed side-by-side:
- **Opposite poles attract** (`...01` followed by `10...` or `...10` followed by `01...`), joining together to form a single continuous group.
- **Like poles repel** (`...01` followed by `01...` or `...10` followed by `10...`), creating a physical separation and starting a new group.

Determine the total number of groups formed after laying all $n$ magnets in a row.

**Input:**
- The first line contains an integer $n$ ($1 \le n \le 100\,000$) — the number of magnets.
- The next $n$ lines each contain a 2-character string: `"01"` or `"10"`.

**Output:**
- Print a single integer — the total number of magnet groups formed.

---

### 💡 Key Insights
1. **Consecutive Group Boundaries:** A new group forms precisely when the orientation of the current magnet differs from the preceding one. 
2. **Linear Scan:** Start with an initial count of `1` (representing the first group). Iterate through the remaining $n - 1$ magnets, comparing each magnet with the previous one. Increment the count whenever `curr != prev`.
3. **Time & Space Efficiency:** A single pass takes $O(n)$ time using $O(1)$ auxiliary memory by storing only the previous magnet's configuration instead of saving the entire array.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Magnets (Codeforces 344A)
 * Language: Java 17 / 21
 */
public class Magnets {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String firstLine = reader.readLine();
        if (firstLine == null || firstLine.trim().isEmpty()) {
            return;
        }

        int n = Integer.parseInt(firstLine.trim());
        if (n == 0) {
            System.out.println(0);
            return;
        }

        int groups = 1;
        String prev = reader.readLine().trim();

        for (int i = 1; i < n; i++) {
            String curr = reader.readLine().trim();
            if (!curr.equals(prev)) {
                groups++;
                prev = curr;
            }
        }

        System.out.println(groups);
    }
}
```
---

### ⏱️ Complexity Analysis

| Metric | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | We perform a single linear scan through the $n$ magnet strings. |
| **Space Complexity** | $\mathcal{O}(1)$ | Only constant extra memory is used to store `prev` and `curr` strings without allocating an array. |
