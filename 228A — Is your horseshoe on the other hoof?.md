# 🐴 Codeforces 228A — Is your horseshoe on the other hoof?

### 📝 Problem Description
Valera the Horse is going to a party with friends. To stay trendy, he needs to wear four horseshoes of completely distinct colors. Valera already has four horseshoes from last year, but some might share the same color. 

Determine the minimum number of additional horseshoes he must buy so that he wears four horseshoes of different colors.

**Input:**
- A single line containing four space-separated integers $s_1, s_2, s_3, s_4$ ($1 \le s_1, s_2, s_3, s_4 \le 10^9$) representing the colors of the horseshoes Valera currently owns.

**Output:**
- Print a single integer — the minimum number of horseshoes Valera needs to purchase.

---

### 💡 Key Insights
1. **Goal:** Valera must end up with $4$ distinct colors.
2. **Finding Unique Colors:** Valera should keep exactly one horseshoe for every distinct color he already has. If he has $u$ unique colors among his original four horseshoes, he keeps $u$ of them.
3. **Calculating Purchases:** The remaining $4 - u$ horseshoes are duplicates, which means he must buy exactly $4 - u$ new horseshoes of different colors.
4. **Data Structures:** A `HashSet` naturally filters duplicate values and provides the count of unique elements in $O(1)$ amortized time.
5. **Time & Space Complexity:**
   - **Time Complexity:** $O(1)$ — processing exactly $4$ elements.
   - **Space Complexity:** $O(1)$ — storing at most $4$ integers in a set.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.HashSet;
import java.util.Set;
import java.util.StringTokenizer;

/**
 * Problem: Is your horseshoe on the other hoof? (Codeforces 228A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class Horseshoe {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        String line = reader.readLine();

        if (line == null || line.trim().isEmpty()) {
            return;
        }

        StringTokenizer tokenizer = new StringTokenizer(line);
        Set<Integer> uniqueColors = new HashSet<>();

        while (tokenizer.hasMoreTokens()) {
            uniqueColors.add(Integer.parseInt(tokenizer.nextToken()));
        }

        System.out.println(4 - uniqueColors.size());
    }
}
```
### ⏱️ Complexity Analysis

| Metric | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(1)$ | Reading input and performing lookups/insertions for exactly $4$ elements runs in constant time. |
| **Space Complexity** | $\mathcal{O}(1)$ | The `HashSet` stores at most $4$ distinct integer values, requiring constant extra memory. |
