# ⚡ Codeforces 158B — Taxi

### 📝 Problem Description
After the lessons $n$ groups of schoolchildren went outside and decided to visit Polycarpus to celebrate his birthday. We know that the $i$-th group consists of $s_i$ friends ($1 \le s_i \le 4$), and they want to go to Polycarpus together. 

They decided to get there by taxi. Each car can carry at most four passengers. What minimum number of cars will the children need if all members of each group should ride in the same taxi (but one taxi can take more than one group)?

**Input:**
- The first line contains an integer $n$ ($1 \le n \le 10^5$) — the number of groups of schoolchildren.
- The second line contains a sequence of integers $s_1, s_2, \dots, s_n$ ($1 \le s_i \le 4$). The integers are separated by a space, where $s_i$ is the number of children in the $i$-th group.

**Output:**
- Print a single number — the minimum number of taxis necessary to drive all children to Polycarpus.

---

### 💡 Key Insights
1. **Frequency Counting:**
   - Because each group size $s_i \in \{1, 2, 3, 4\}$, we can count occurrences of each group size into four buckets: `count[1]`, `count[2]`, `count[3]`, and `count[4]`.

2. **Greedy Matching Strategy:**
   - **Groups of 4 (`count[4]`):** Each group of 4 fills an entire taxi alone.
   - **Groups of 3 (`count[3]`):** Each group of 3 requires a taxi and leaves 1 spare seat. Greedily pair each group of 3 with a group of 1 to utilize this empty seat. If not enough 1s exist, the group of 3 still takes a full taxi.
   - **Groups of 2 (`count[2]`):** Two groups of size 2 fit perfectly into one taxi ($2 + 2 = 4$). 
     - If an odd group of 2 remains (`count[2] % 2 == 1`), it takes another taxi with 2 empty seats remaining. 
     - Greedily place up to two groups of 1 into these remaining seats.
   - **Remaining Groups of 1 (`count[1]`):** Any leftover groups of 1 are packed 4 per taxi, which requires $\lceil \text{count}[1] / 4 \rceil = \lfloor (\text{count}[1] + 3) / 4 \rfloor$ additional taxis.

3. **Constraints & Efficiency:**
   - $n \le 10^5$, so an $\mathcal{O}(n)$ frequency-count pass followed by an $\mathcal{O}(1)$ arithmetic packing runs in well under the standard time limit.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Taxi (Codeforces 158B)
 * Language: Java 8 / 11 / 17 / 21
 */
public class Taxi {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        String line = reader.readLine();
        if (line == null || line.trim().isEmpty()) {
            return;
        }

        int n = Integer.parseInt(line.trim());
        int[] count = new int[5];

        StringTokenizer st = new StringTokenizer(reader.readLine());
        for (int i = 0; i < n; i++) {
            count[Integer.parseInt(st.nextToken())]++;
        }

        // Step 1: Groups of 4 each require a separate taxi
        int taxis = count[4];

        // Step 2: Groups of 3 each take a taxi, greedily paired with groups of 1
        taxis += count[3];
        count[1] = Math.max(0, count[1] - count[3]);

        // Step 3: Groups of 2 pair together (2 + 2 = 4)
        taxis += count[2] / 2;
        count[2] %= 2;

        // Step 4: If one group of 2 remains, it shares a taxi with up to two 1s
        if (count[2] > 0) {
            taxis++;
            count[1] = Math.max(0, count[1] - 2);
        }

        // Step 5: Pack any remaining groups of 1 into taxis of 4
        if (count[1] > 0) {
            taxis += (count[1] + 3) / 4;
        }

        System.out.println(taxis);
    }
}
```
| Metric | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | Single pass over $n \le 10^5$ elements to build the frequency array, followed by $\mathcal{O}(1)$ greedy pairing. |
| **Space Complexity (Auxiliary)** | $\mathcal{O}(1)$ | Fixed-size frequency array of length $5$ and a few primitive counters. |
| **Space Complexity (Input Parsing)** | $\mathcal{O}(n)$ | Line buffer memory used by `BufferedReader` and `StringTokenizer` during I/O. |
