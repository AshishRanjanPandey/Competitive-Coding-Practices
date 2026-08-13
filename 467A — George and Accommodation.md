# 🚀 Codeforces 467A — George and Accommodation

### 📝 Problem Description
George has recently entered the BSUCP (Berland State University for Cool Programmers). George has a friend Alex who has also entered the university. Now they are moving into a dormitory.

George and Alex want to live in the same room. The dormitory has $n$ rooms in total. At the moment the $i$-th room has $p_i$ people living in it and the room can accommodate $q_i$ people in total ($p_i \le q_i$). Your task is to count how many rooms have free places for both George and Alex.

**Input:**
- The first line contains a single integer $n$ ($1 \le n \le 100$) — the number of rooms.
- The $i$-th of the next $n$ lines contains two integers $p_i$ and $q_i$ ($0 \le p_i \le q_i \le 100$) — the number of people who already live in the $i$-th room and the room's total capacity.

**Output:**
- Print a single integer — the number of rooms where George and Alex can move in together.

---

### 💡 Key Insights
1. **Condition Check:** For both George and Alex to move into a room, the room needs to have at least **2 free spots**.
2. **Mathematical Formulation:** A room $i$ has $q_i - p_i$ available spots. Thus, the condition to check for each room is $q_i - p_i \ge 2$.
3. **Time & Space Efficiency:** We process each room's capacity on the fly as we read the input. This runs in $O(n)$ time using $O(1)$ auxiliary space.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: George and Accommodation (Codeforces 467A)
 * Language: Java 17
 */
public class GeorgeAndAccommodation {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String line = reader.readLine();
        if (line == null) {
            return;
        }
        
        int n = Integer.parseInt(line.trim());
        int count = 0;
        
        for (int i = 0; i < n; i++) {
            StringTokenizer st = new StringTokenizer(reader.readLine());
            int p = Integer.parseInt(st.nextToken()); // Currently living
            int q = Integer.parseInt(st.nextToken()); // Total capacity
            
            // Check if there is space for at least 2 people (George and Alex)
            if (q - p >= 2) {
                count++;
            }
        }
        
        System.out.println(count);
    }
}
```
| Metric | Complexity | Description |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | We iterate through the $n$ rooms once, processing input in constant time per room. |
| **Space Complexity** | $\mathcal{O}(1)$ | Uses a fixed amount of auxiliary memory regardless of the input size $n$. |
