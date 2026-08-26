# ⚡ Codeforces 405A — Gravity Flip

### 📝 Problem Description
Little Chris is bored during his physics lessons (too easy), so he has built a toy box to keep himself occupied. The box is special, since it has the ability to change gravity.

There are $n$ columns of toy cubes in the box arranged in a line. The $i$-th column contains $a_i$ cubes. At first, the gravity in the box is pulling the cubes downwards. When Chris switches the gravity, it begins to pull all the cubes to the right side of the box.

Given the initial configuration of the toy cubes in the box, find the amounts of cubes in each of the $n$ columns after the gravity switch!

**Input:**
- The first line contains an integer $n$ ($1 \le n \le 100$) — the number of columns in the box.
- The next line contains $n$ space-separated integers $a_1, a_2, \dots, a_n$ ($1 \le a_i \le 100$), where $a_i$ denotes the number of cubes in the $i$-th column.

**Output:**
- Output $n$ integer numbers separated by spaces, where the $i$-th number is the amount of cubes in the $i$-th column after the gravity switch.

---

### 💡 Key Insights
1. **Physical Intuition to Mathematical Sort:**
   - When gravity shifts from downward to rightward, every individual cube falls as far to the right as possible.
   - A cube at height $h$ in column $i$ will slide horizontally until it hits either the right wall or another cube resting at height $h$.
   - Consequently, earlier columns will retain fewer cubes while later columns accumulate the maximum possible cubes. This makes the resulting column heights monotonically non-decreasing.
2. **Equivalence to Array Sorting:**
   - The end state after the gravity flip simply corresponds to sorting the initial heights array $a$ in ascending order.
3. **Complexity:**
   - **Time Complexity:** $\mathcal{O}(n \log n)$ — sorting an array of size up to $100$ takes negligible time and executes well within the $1.0$-second limit.
   - **Space Complexity:** $\mathcal{O}(n)$ — required to store the initial column counts.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.Arrays;
import java.util.StringTokenizer;

/**
 * Problem: Gravity Flip (Codeforces 405A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class GravityFlip {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String nLine = reader.readLine();
        if (nLine == null) {
            return;
        }
        
        int n = Integer.parseInt(nLine.trim());
        int[] a = new int[n];
        
        StringTokenizer tokenizer = new StringTokenizer(reader.readLine());
        for (int i = 0; i < n; i++) {
            a[i] = Integer.parseInt(tokenizer.nextToken());
        }
        
        // When cubes slide to the right, heights end up sorted in non-decreasing order
        Arrays.sort(a);
        
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < n; i++) {
            sb.append(a[i]);
            if (i < n - 1) {
                sb.append(" ");
            }
        }
        
        System.out.println(sb.toString());
    }
}
```
### 📊 Complexity Analysis

| Metric | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n \log n)$ | Reading input takes $\mathcal{O}(n)$ and sorting the array of size $n$ using Dual-Pivot Quicksort takes $\mathcal{O}(n \log n)$. With $n \le 100$, this executes in $< 1\text{ ms}$. |
| **Auxiliary Space** | $\mathcal{O}(n)$ | Required to store the $n$ column heights in the integer array `a` and buffer the output string via `StringBuilder`. |
| **Sorting Space** | $\mathcal{O}(\log n)$ | Call stack space for primitive array sorting (`Arrays.sort`). |
