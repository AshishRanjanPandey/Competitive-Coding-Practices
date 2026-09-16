# 🚀 Codeforces 230A — Dragons

### 📝 Problem Description
Kirito is stuck on a level of an MMORPG. To progress to the next level, he must defeat all $n$ dragons residing on this level. Both Kirito and the dragons have strengths represented by integers. In a duel, the outcome depends strictly on their strengths. Initially, Kirito's strength equals $s$.

If Kirito fights the $i$-th dragon ($1 \le i \le n$) and his strength is not strictly greater than the dragon's strength $x_i$, Kirito loses and dies. If Kirito's strength is strictly greater than $x_i$, he defeats the dragon and gains a bonus strength increase of $y_i$.

Kirito is allowed to fight the dragons in any order. Determine whether he can defeat all $n$ dragons without losing a single duel and advance to the next level.

**Input:**
- The first line contains two space-separated integers $s$ and $n$ ($1 \le s \le 10^4$, $1 \le n \le 10^3$) — Kirito's initial strength and the number of dragons.
- The next $n$ lines each contain two space-separated integers $x_i$ and $y_i$ ($1 \le x_i \le 10^4$, $0 \le y_i \le 10^4$) — the strength of the $i$-th dragon and the strength bonus gained upon defeating it.

**Output:**
- Print `"YES"` (without quotes) if Kirito can defeat all dragons, or `"NO"` (without quotes) if he cannot.

---

### 💡 Key Insights
1. **Greedy Choice Property:** To maximize Kirito's chances of defeating all dragons, he should always fight the weakest available dragon first (the one requiring the lowest strength $x_i$). Defeating weaker dragons grants bonuses $y_i$, which monotonically increases Kirito's strength and helps him face stronger foes later.
2. **Sorting Strategy:** Pair each dragon's required strength $x_i$ with its bonus $y_i$, then sort all dragons in non-decreasing order of $x_i$.
3. **Simulation & Early Exit:** Iterate through the sorted list. At each step, check if Kirito's current strength $s > x_i$. If it is, increment $s$ by $y_i$. If $s \le x_i$, Kirito cannot defeat this dragon or any subsequent stronger dragons; output `"NO"` immediately. If all dragons are defeated, output `"YES"`.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.Arrays;
import java.util.StringTokenizer;

/**
 * Problem: Dragons (Codeforces 230A)
 * Language: Java 17
 */
public class Dragons {

    static class Dragon implements Comparable<Dragon> {
        int strength;
        int bonus;

        Dragon(int strength, int bonus) {
            this.strength = strength;
            this.bonus = bonus;
        }

        @Override
        public int compareTo(Dragon other) {
            return Integer.compare(this.strength, other.strength);
        }
    }

    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        String line = reader.readLine();
        if (line == null) {
            return;
        }

        StringTokenizer st = new StringTokenizer(line);
        int s = Integer.parseInt(st.nextToken());
        int n = Integer.parseInt(st.nextToken());

        Dragon[] dragons = new Dragon[n];
        for (int i = 0; i < n; i++) {
            st = new StringTokenizer(reader.readLine());
            int x = Integer.parseInt(st.nextToken());
            int y = Integer.parseInt(st.nextToken());
            dragons[i] = new Dragon(x, y);
        }

        // Sort dragons by required strength ascending
        Arrays.sort(dragons);

        boolean canDefeatAll = true;
        for (int i = 0; i < n; i++) {
            if (s > dragons[i].strength) {
                s += dragons[i].bonus;
            } else {
                canDefeatAll = false;
                break;
            }
        }

        if (canDefeatAll) {
            System.out.println("YES");
        } else {
            System.out.println("NO");
        }
    }
}
```
### 📊 Complexity Analysis

| Metric | Complexity | Description |
| :--- | :---: | :--- |
| **Sorting Dragons** | $\mathcal{O}(n \log n)$ | Dual-Pivot Quicksort via `Arrays.sort()` on the $n$ dragon entries. |
| **Linear Simulation** | $\mathcal{O}(n)$ | Single pass over the sorted array to verify fights and accumulate bonuses. |
| **Total Time Complexity** | $\mathcal{O}(n \log n)$ | Dominated by sorting; executes in under 0.15s for $n \le 10^3$. |
| **Auxiliary Space** | $\mathcal{O}(n)$ | Memory used to store the array of $n$ `Dragon` objects. |
