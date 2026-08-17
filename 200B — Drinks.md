# 🍊 Codeforces 200B — Drinks

### 📝 Problem Description
Little Vasya loves orange juice very much. There are $n$ drinks in his fridge, where the volume fraction of orange juice in the $i$-th drink equals $p_i$ percent.

Vasya decides to make a cocktail by taking equal proportions of each of the $n$ drinks and mixing them together. Find the volume fraction (in percent) of orange juice in the final cocktail.

**Input:**
- The first line contains an integer $n$ ($1 \le n \le 100$) — the number of drinks in the fridge.
- The second line contains $n$ integers $p_i$ ($0 \le p_i \le 100$) — the volume fraction of orange juice in each drink, in percent.

**Output:**
- Print the volume fraction of orange juice in the final cocktail in percent. The solution is considered correct if its absolute or relative error does not exceed $10^{-4}$.

---

### 💡 Key Insights
1. **Equal Proportions:** Since equal volumes $V$ of each of the $n$ drinks are mixed, the total volume of cocktail is $n \cdot V$.
2. **Total Juice Volume:** The total volume of pure orange juice across all drinks is:
   $$\sum_{i=1}^n \left(V \cdot \frac{p_i}{100}\right) = \frac{V}{100} \sum_{i=1}^n p_i$$
3. **Arithmetic Mean:** The final volume percentage simplifies directly to the average of all given percentages:
   $$\text{Final Percentage} = \frac{\sum_{i=1}^n p_i}{n}$$
4. **Time & Space Complexity:**
   - **Time Complexity:** $O(n)$ to sum the input values.
   - **Space Complexity:** $O(1)$ auxiliary space.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Drinks (Codeforces 200B)
 * Language: Java 17 / 21
 */
public class Drinks {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String line = reader.readLine();
        if (line == null || line.trim().isEmpty()) {
            return;
        }

        int n = Integer.parseInt(line.trim());
        
        StringTokenizer tokenizer = new StringTokenizer(reader.readLine());
        double totalPercentageSum = 0.0;
        
        for (int i = 0; i < n; i++) {
            totalPercentageSum += Double.parseDouble(tokenizer.nextToken());
        }
        
        double result = totalPercentageSum / n;
        
        // Print formatted result with sufficient floating-point precision
        System.out.printf("%.12f\n", result);
    }
}
```
### ⏱️ Complexity Analysis

| Type | Complexity | Explanation |
| :--- | :---: | :--- |
| **Time Complexity** | $O(n)$ | We iterate through the $n$ drink percentages exactly once to compute the sum. |
| **Space Complexity** | $O(1)$ | Memory usage is constant; input is accumulated on the fly without storing an array. |
