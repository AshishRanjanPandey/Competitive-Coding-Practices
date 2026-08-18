# 🎁 Codeforces 136A — Presents

### 📝 Problem Description
Little Petya very much likes gifts. He invited $n$ friends to his New Year party, numbered from $1$ to $n$. Petya remembered that friend number $i$ gave a gift to friend number $p_i$. He also remembered that each of his friends received exactly one gift.

Now Petya wants to know for each friend $i$ the number of the friend who gave them a gift.

**Input:**
- The first line contains an integer $n$ ($1 \le n \le 100$) — the number of friends invited.
- The second line contains $n$ space-separated integers $p_1, p_2, \dots, p_n$ ($1 \le p_i \le n$), where $p_i$ is the number of the friend who received a gift from friend $i$.

**Output:**
- Print $n$ space-separated integers, where the $i$-th integer is the number of the friend who gave a gift to friend $i$.

---

### 💡 Key Insights
1. **Permutation Inversion:** The problem asks to compute the inverse of a given permutation. If friend $i$ gave a gift to friend $p_i$, then the giver for recipient $p_i$ is $i$.
2. **Direct Mapping:** Use an array `giverOf` of size $n + 1$. While processing each 1-based index $i$ from $1$ to $n$ and reading recipient $p_i$, assign:
   $$\text{giverOf}[p_i] = i$$
3. **One-Pass Output:** After reading all inputs, iterate from $1$ to $n$ and print $\text{giverOf}[i]$.
4. **Complexity:**
   - **Time Complexity:** $\mathcal{O}(n)$ — reads input and writes output in a single linear pass.
   - **Space Complexity:** $\mathcal{O}(n)$ — auxiliary array of size $n + 1$ to store the inverse mappings.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Presents (Codeforces 136A)
 * Language: Java 17 / 21
 */
public class Presents {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String firstLine = reader.readLine();
        if (firstLine == null || firstLine.trim().isEmpty()) {
            return;
        }

        int n = Integer.parseInt(firstLine.trim());
        int[] giverOf = new int[n + 1];

        StringTokenizer tokenizer = new StringTokenizer(reader.readLine());
        for (int giver = 1; giver <= n; giver++) {
            int receiver = Integer.parseInt(tokenizer.nextToken());
            giverOf[receiver] = giver;
        }

        StringBuilder sb = new StringBuilder();
        for (int i = 1; i <= n; i++) {
            sb.append(giverOf[i]).append(i == n ? "" : " ");
        }

        System.out.println(sb.toString());
    }
}
```
### ⏱️ Complexity Analysis

| Metric | Complexity | Description |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | Single linear pass to read $n$ inputs and map indices, plus one pass to format the output. |
| **Space Complexity** | $\mathcal{O}(n)$ | Requires an auxiliary array of size $n + 1$ to store the inverted permutation. |
