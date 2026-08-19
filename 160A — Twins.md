# 🪙 Codeforces 160A — Twins

### 📝 Problem Description
Imagine that you have a twin brother or sister. Your Mom left $n$ coins of arbitrary values $a_1, a_2, \dots, a_n$ for both of you to buy school lunches. She scribbled a note asking you to split the money equally.

However, you decide to act selfishly: pick a subset of coins such that the sum of values of your coins is **strictly greater** than the sum of values of the remaining coins your twin gets. To avoid suspicion, you want to take the **minimum number of coins** possible that satisfies this condition.

**Input:**
- The first line contains an integer $n$ ($1 \le n \le 100$) — the number of coins.
- The second line contains $n$ integers $a_1, a_2, \dots, a_n$ ($1 \le a_i \le 100$) — the values of the coins.

**Output:**
- Print a single integer — the minimum number of coins needed so that your sum is strictly greater than your twin's sum.

---

### 💡 Key Insights
1. **Greedy Strategy:** To minimize the *number* of coins taken while maximizing the *total value* obtained, always pick the coins with the highest values first.
2. **Strict Condition:** You need:
   $$\text{mySum} > \text{totalSum} - \text{mySum} \iff \text{mySum} > \frac{\text{totalSum}}{2}$$
3. **Algorithm:**
   - Compute $\text{totalSum} = \sum_{i=1}^n a_i$.
   - Sort the coin array in ascending order.
   - Iterate from the largest element down to the smallest, accumulating $\text{mySum}$ and incrementing $\text{coinCount}$.
   - Stop as soon as $\text{mySum} > \text{totalSum} - \text{mySum}$.
4. **Complexity:**
   - **Time Complexity:** $O(n \log n)$ due to sorting the array of size $n \le 100$.
   - **Space Complexity:** $O(n)$ to store the array of coin values.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.Arrays;
import java.util.StringTokenizer;

/**
 * Problem: Twins (Codeforces 160A)
 * Language: Java 17 / 21
 */
public class Twins {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String line = reader.readLine();
        if (line == null || line.trim().isEmpty()) {
            return;
        }

        int n = Integer.parseInt(line.trim());
        int[] coins = new int[n];
        int totalSum = 0;

        StringTokenizer tokenizer = new StringTokenizer(reader.readLine());
        for (int i = 0; i < n; i++) {
            coins[i] = Integer.parseInt(tokenizer.nextToken());
            totalSum += coins[i];
        }

        // Sort coins in non-decreasing order
        Arrays.sort(coins);

        int mySum = 0;
        int count = 0;

        // Greedily take the largest coins from the end of the array
        for (int i = n - 1; i >= 0; i--) {
            mySum += coins[i];
            count++;

            // Stop once our sum is strictly greater than the remaining coins
            if (mySum > totalSum - mySum) {
                break;
            }
        }

        System.out.println(count);
    }
}
```
### 📊 Complexity Analysis

| Metric | Complexity | Details |
| :--- | :---: | :--- |
| **Time Complexity** | $\mathcal{O}(n \log n)$ | Dominated by sorting $n$ coins (`Arrays.sort()`). The subsequent reverse greedy scan runs in $\mathcal{O}(n)$ time. |
| **Space Complexity** | $\mathcal{O}(n)$ | Required to store the $n$ coin values in an integer array. |
| **Auxiliary Space** | $\mathcal{O}(\log n)$ | Space overhead used by Java's Dual-Pivot Quicksort recursion stack. |
