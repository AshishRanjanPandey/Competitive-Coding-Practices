# ⚡ Codeforces 144A — Arrival of the General

### 📝 Problem Description
A Ministry for Defense sent a general to inspect the Super Secret Military Squad under the command of Colonel SuperDuper. Having learned the news, the colonel ordered all $n$ squad soldiers to line up on the parade ground.

The general is rather short-sighted and thinks that the soldiers lined up correctly if the first soldier in the line has the maximum height and the last soldier has the minimum height. The way other soldiers are positioned does not matter. If there are multiple soldiers with the maximum or minimum height, only the heights of the first and the last soldier in the line are important.

Within one second, the colonel can swap any two neighboring soldiers. Help him count the minimum time needed to form a line-up which the general will consider correct.

**Input:**
- The first line contains a single integer $n$ ($2 \le n \le 100$) — the number of soldiers in the line.
- The second line contains integers $a_1, a_2, \dots, a_n$ ($1 \le a_i \le 100$) — the values of the soldiers' heights.

**Output:**
- Print a single integer — the minimum number of seconds the colonel will need to form a line-up the general will like.

---

### 💡 Key Insights
1. **Target Positions:**
   - The soldier with the **maximum height** needs to move to index `0` (front of the line). To minimize swaps, we pick the **first (leftmost) occurrence** of the maximum height (`max_idx`).
   - The soldier with the **minimum height** needs to move to index `n - 1` (end of the line). To minimize swaps, we pick the **last (rightmost) occurrence** of the minimum height (`min_idx`).

2. **Calculating Swaps:**
   - Moving the maximum element from `max_idx` to `0` takes `max_idx` swaps.
   - Moving the minimum element from `min_idx` to `n - 1` takes `(n - 1) - min_idx` swaps.

3. **Crossing Over:**
   - If `max_idx > min_idx`, the maximum element will pass over the minimum element while being swapped leftward. This swap shifts the minimum element one position to the right automatically.
   - Therefore, when `max_idx > min_idx`, we subtract `1` from the total number of swaps:
     $$\text{Total Swaps} = \text{max\_idx} + (n - 1 - \text{min\_idx}) - (\text{max\_idx} > \text{min\_idx} \text{ ? } 1 : 0)$$

4. **Complexity:**
   - **Time Complexity:** $\mathcal{O}(n)$ — a single pass across the array of length up to $100$ runs well within the $2.0$-second time limit.
   - **Space Complexity:** $\mathcal{O}(n)$ — to store the heights of the soldiers.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Arrival of the General (Codeforces 144A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class ArrivalOfTheGeneral {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String nLine = reader.readLine();
        if (nLine == null) {
            return;
        }
        
        int n = Integer.parseInt(nLine.trim());
        StringTokenizer tokenizer = new StringTokenizer(reader.readLine());
        
        int[] a = new int[n];
        int maxVal = Integer.MIN_VALUE;
        int minVal = Integer.MAX_VALUE;
        int maxIdx = 0;
        int minIdx = 0;
        
        for (int i = 0; i < n; i++) {
            a[i] = Integer.parseInt(tokenizer.nextToken());
            
            // First (leftmost) occurrence of the maximum element
            if (a[i] > maxVal) {
                maxVal = a[i];
                maxIdx = i;
            }
            
            // Last (rightmost) occurrence of the minimum element
            if (a[i] <= minVal) {
                minVal = a[i];
                minIdx = i;
            }
        }
        
        int swaps = maxIdx + (n - 1 - minIdx);
        
        // If the max element is to the right of the min element,
        // they cross paths, saving 1 swap.
        if (maxIdx > minIdx) {
            swaps--;
        }
        
        System.out.println(swaps);
    }
}
```
### 📊 Complexity Analysis

| Metric | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | Single pass over the array of size $n$ to find `max_idx` and `min_idx`. |
| **Space Complexity** | $\mathcal{O}(n)$ | To store the array of size $n$ (can be optimized to $\mathcal{O}(1)$ without storing the array). |
