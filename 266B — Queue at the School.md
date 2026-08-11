# 🚀 Codeforces 266B — Queue at the School

### 📝 Problem Description
During the break, the schoolchildren formed a queue of $n$ people in the canteen. Initially, the children stood in the order they entered. However, after a while, the boys started feeling awkward standing in front of the girls, so they began letting the girls move forward every second.

Specifically, if at second $x$ a boy stands at position $i$ and a girl stands at position $i + 1$, then at second $x + 1$ position $i$ will contain the girl and position $i + 1$ will contain the boy.

Given the initial positions of the children, determine what the queue looks like after $t$ seconds.

**Input:**
- The first line contains two integers $n$ and $t$ ($1 \le n, t \le 50$) — the number of children in the queue and the time in seconds.
- The second line contains a string $s$ of length $n$ consisting of `'B'` (Boy) and `'G'` (Girl), representing the initial queue arrangement.

**Output:**
- Print a string of length $n$ representing the queue arrangement after $t$ seconds.

---

### 💡 Key Insights
1. **Adjacent Swaps Simulation:** Every second, we iterate from left to right through the queue string and search for adjacent pairs matching the pattern `"BG"`.
2. **Avoiding Double-Swaps:** When a `"BG"` pair is found, we swap them to `"GB"`. To ensure the same boy doesn't move forward twice within the same single second, we must advance our loop index by an extra step (`i++`).
3. **Time & Space Complexity:** Since $n, t \le 50$, simulating the swaps takes at most $\mathcal{O}(n \cdot t)$ operations (roughly $2500$ iterations max), running virtually instantaneously in $\mathcal{O}(n)$ auxiliary space.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Queue at the School (Codeforces 266B)
 * Language: Java 17
 */
public class QueueAtTheSchool {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String line = reader.readLine();
        if (line == null) {
            return;
        }
        
        StringTokenizer st = new StringTokenizer(line);
        int n = Integer.parseInt(st.nextToken());
        int t = Integer.parseInt(st.nextToken());
        
        char[] queue = reader.readLine().trim().toCharArray();
        
        // Simulate the queue process for t seconds
        for (int second = 0; second < t; second++) {
            for (int i = 0; i < n - 1; i++) {
                if (queue[i] == 'B' && queue[i + 1] == 'G') {
                    // Swap 'B' and 'G'
                    queue[i] = 'G';
                    queue[i + 1] = 'B';
                    
                    // Skip the next position so the boy moves only 1 step per second
                    i++;
                }
            }
        }
        
        System.out.println(new String(queue));
    }
}
```
### 📊 Complexity Analysis

| Type | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n \cdot t)$ | Outer loop runs $t$ times and inner loop iterates up to $n - 1$ times per second. Max operations $\approx 50 \times 50 = 2500$. |
| **Space Complexity** | $\mathcal{O}(n)$ | Auxiliary memory used to store the queue string in a character array of size $n$. |

---
