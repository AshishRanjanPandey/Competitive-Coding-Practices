# 🚀 Codeforces 337A — Puzzles

### 📝 Problem Description
The end of the school year is near and Ms. Manana, the teacher, will soon have to say goodbye to yet another class. She decided to prepare a goodbye present for her $n$ students and give each of them a jigsaw puzzle.

The shop assistant told the teacher that there are $m$ puzzles in the shop, but they might differ in difficulty and size. Specifically, the first jigsaw puzzle consists of $f_1$ pieces, the second one consists of $f_2$ pieces, and so on.

Ms. Manana doesn't want to upset the children, so she decided that the difference between the numbers of pieces in her presents must be as small as possible. Let $A$ be the number of pieces in the largest puzzle that the teacher buys and $B$ be the number of pieces in the smallest such puzzle. She wants to choose such $n$ puzzles that $A - B$ is the minimum possible. Help the teacher and find the least possible value of $A - B$.

**Input:**
- The first line contains two space-separated integers $n$ and $m$ ($2 \le n \le m \le 50$) — the number of students and the number of puzzles sold in the shop.
- The second line contains $m$ space-separated integers $f_1, f_2, \dots, f_m$ ($4 \le f_i \le 1000$) — the quantities of pieces in the puzzles sold in the shop.

**Output:**
- Print a single integer — the least possible difference $A - B$ the teacher can obtain.

---

### 💡 Key Insights
1. **Sorting Simplification:** If the puzzles are sorted in non-decreasing order, any optimal selection of $n$ puzzles will always form a contiguous subarray. Selecting non-contiguous elements could only increase or keep the difference between the maximum and minimum values identical.
2. **Fixed-Size Sliding Window:** After sorting the array $f$, every candidate subset of size $n$ can be represented as a window $[i, i + n - 1]$ for all $0 \le i \le m - n$.
3. **Local Evaluation:** For each window, the smallest element is $f[i]$ and the largest is $f[i + n - 1]$. The local difference is simply $f[i + n - 1] - f[i]$. We iterate through all valid starting positions $i$ and maintain the global minimum difference.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.Arrays;
import java.util.StringTokenizer;

/**
 * Problem: Puzzles (Codeforces 337A)
 * Language: Java 17 / 21
 */
public class Puzzles {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String firstLine = reader.readLine();
        if (firstLine == null) {
            return;
        }
        
        StringTokenizer st = new StringTokenizer(firstLine);
        int n = Integer.parseInt(st.nextToken());
        int m = Integer.parseInt(st.nextToken());
        
        int[] f = new int[m];
        st = new StringTokenizer(reader.readLine());
        for (int i = 0; i < m; i++) {
            f[i] = Integer.parseInt(st.nextToken());
        }
        
        // Sort the puzzle piece counts in ascending order
        Arrays.sort(f);
        
        int minDiff = Integer.MAX_VALUE;
        
        // Slide a window of size n across the sorted array
        for (int i = 0; i <= m - n; i++) {
            int currentDiff = f[i + n - 1] - f[i];
            if (currentDiff < minDiff) {
                minDiff = currentDiff;
            }
        }
        
        System.out.println(minDiff);
    }
}
```
| Metric | Complexity | Details |
| :--- | :--- | :--- |
| **Time (Sorting)** | $\mathcal{O}(m \log m)$ | Dual-pivot Quicksort (`Arrays.sort`) on the array of $m$ puzzle sizes. |
| **Time (Sliding Window)** | $\mathcal{O}(m - n)$ | Single linear pass checking all windows of length $n$. |
| **Total Time Complexity** | $\mathcal{O}(m \log m)$ | Dominated by sorting; executes in $< 1 \text{ ms}$ for $m \le 50$. |
| **Auxiliary Space** | $\mathcal{O}(m)$ | Primitive array `f` to hold the $m$ puzzle piece counts. |
