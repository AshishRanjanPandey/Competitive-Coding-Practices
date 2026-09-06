# ⚡ Codeforces 580A — Kefa and First Steps

### 📝 Problem Description
Kefa decided to make some money doing business on the Internet for exactly $n$ days. He knows that on the $i$-th day ($1 \le i \le n$) he makes $a_i$ money. Kefa loves progress, that's why he wants to know the length of the maximum non-decreasing subsegment in sequence $a_i$. 

Let us remind you that a subsegment of the sequence is its continuous fragment. A subsegment of numbers is called non-decreasing if all numbers in it follow in non-decreasing order ($a_l \le a_{l+1} \le \dots \le a_r$).

Your task is: given $n$ and sequence $a$, print the length of the maximum non-decreasing subsegment of sequence $a$.

**Input:**
- The first line contains an integer $n$ ($1 \le n \le 10^5$).
- The second line contains $n$ integers $a_1, a_2, \dots, a_n$ ($1 \le a_i \le 10^9$).

**Output:**
- Print a single integer — the length of the maximum non-decreasing subsegment of sequence $a$.

---

### 💡 Key Insights
1. **Contiguous Subsegment:**
   - The problem asks for a continuous subarray (subsegment), not a general subsequence. This means we only need to compare each element with its immediate predecessor $a[i - 1]$.

2. **Single-Pass Greedy Tracking:**
   - Any single element forms a non-decreasing subsegment of length $1$, so initialize `currentLength = 1` and `maxLength = 1`.
   - Iterate from the second element ($i = 1$) to the end:
     - If $a[i] \ge a[i - 1]$, extend the current subsegment: `currentLength++`.
     - If $a[i] < a[i - 1]$, the run breaks: reset `currentLength = 1`.
     - Update the global maximum at every step: `maxLength = Math.max(maxLength, currentLength)`.

3. **Edge Cases:**
   - When $n = 1$, the loop does not run, and the answer is correctly $1$.
   - When the whole array is strictly decreasing (e.g., `5 4 3 2 1`), `currentLength` never exceeds $1$, and `maxLength` correctly remains $1$.
   - When the array is non-decreasing throughout (e.g., `2 2 9`), updating `maxLength` on each step ensures the trailing run is fully captured.

4. **Complexity:**
   - **Time Complexity:** $\mathcal{O}(n)$ — a single linear scan processes all $n$ values. Fast I/O easily handles $n = 10^5$ well within the 2.0-second limit.
   - **Space Complexity:** $\mathcal{O}(n)$ to store the array (or $\mathcal{O}(1)$ auxiliary space if processed on the fly).

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Kefa and First Steps (Codeforces 580A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class KefaAndFirstSteps {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String firstLine = reader.readLine();
        if (firstLine == null) {
            return;
        }
        
        int n = Integer.parseInt(firstLine.trim());
        int[] arr = new int[n];
        
        StringTokenizer tokenizer = new StringTokenizer(reader.readLine());
        for (int i = 0; i < n; i++) {
            arr[i] = Integer.parseInt(tokenizer.nextToken());
        }
        
        int currentLength = 1;
        int maxLength = 1;
        
        for (int i = 1; i < n; i++) {
            if (arr[i] >= arr[i - 1]) {
                currentLength++;
            } else {
                currentLength = 1;
            }
            maxLength = Math.max(maxLength, currentLength);
        }
        
        System.out.println(maxLength);
    }
}
```
### ⏱️ Complexity Analysis

| Metric | Complexity | Notes |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | Single linear pass through the $n$ elements. Each element is compared with its predecessor once. |
| **Space Complexity** | $\mathcal{O}(n)$ | Array storage for $n$ elements. Can be reduced to $\mathcal{O}(1)$ auxiliary space with streaming I/O. |
