# ⚡ Codeforces 148A — Insomnia Cure

### 📝 Problem Description
«One dragon. Two dragon. Three dragon», — the princess was counting. She had trouble falling asleep, and she got bored of counting lambs when she was nine.

However, just counting dragons was boring as well, so she entertained herself at best she could. Tonight she imagined that all dragons were here to steal her, and she was fighting them off:
- Every $k$-th dragon got punched in the face with a frying pan.
- Every $l$-th dragon got his tail shut into the balcony door.
- Every $m$-th dragon got his paws trampled with sharp heels.
- Finally, she threatened every $n$-th dragon to call her mom, and he withdrew in panic.

How many imaginary dragons suffered moral or physical damage tonight, if the princess counted a total of $d$ dragons?

**Input:**
- Five integers $k, l, m, n, d$, each on a separate line ($1 \le k, l, m, n \le 10$, $1 \le d \le 10^5$).

**Output:**
- Print a single integer — the total number of damaged dragons.

---

### 💡 Key Insights
1. **Damage Condition:**
   - A dragon with index $i$ ($1 \le i \le d$) is damaged if its index is divisible by at least one of the numbers $k, l, m,$ or $n$.
   - Mathematically:
     $$\text{damaged}(i) = (i \bmod k = 0) \lor (i \bmod l = 0) \lor (i \bmod m = 0) \lor (i \bmod n = 0)$$

2. **Direct Simulation:**
   - Because $d \le 10^5$, we can simply iterate through all integers from $1$ to $d$ and maintain a counter for every index that satisfies the damage condition.

3. **Complexity:**
   - **Time Complexity:** $\mathcal{O}(d)$ — iterating $10^5$ times takes only a few milliseconds, well within the $2.0$-second limit.
   - **Space Complexity:** $\mathcal{O}(1)$ — requires only constant extra space for variables.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Insomnia Cure (Codeforces 148A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class InsomniaCure {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String line = reader.readLine();
        if (line == null) {
            return;
        }
        
        int k = Integer.parseInt(line.trim());
        int l = Integer.parseInt(reader.readLine().trim());
        int m = Integer.parseInt(reader.readLine().trim());
        int n = Integer.parseInt(reader.readLine().trim());
        int d = Integer.parseInt(reader.readLine().trim());
        
        int damagedCount = 0;
        
        for (int i = 1; i <= d; i++) {
            if (i % k == 0 || i % l == 0 || i % m == 0 || i % n == 0) {
                damagedCount++;
            }
        }
        
        System.out.println(damagedCount);
    }
}
```
### ⏱️ Complexity Analysis

| Metric | Complexity | Notes |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(d)$ | A single linear loop from $1$ to $d$ ($d \le 10^5$), running in $\approx 10\text{ ms}$. |
| **Space Complexity** | $\mathcal{O}(1)$ | Uses a fixed number of primitive variables with no additional data structures. |
