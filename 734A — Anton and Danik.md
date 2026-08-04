# 🚀 Codeforces 734A — Anton and Danik

### 📝 Problem Description
Anton likes to play chess, and so does his friend Danik. Once they played $n$ games in a row. For each game, it is known who was the winner — Anton or Danik. None of the games ended with a tie.

Now Anton wonders, who won more games, he or Danik? Help him determine this.

**Input:**
- The first line contains a single integer $n$ ($1 \le n \le 100\,000$) — the number of games played.
- The second line contains a string $s$ consisting of $n$ uppercase English letters `'A'` and `'D'` — the outcome of each game. The $i$-th character of the string is equal to `'A'` if Anton won the $i$-th game, and `'D'` if Danik won.

**Output:**
- If Anton won more games than Danik, print `Anton` (without quotes).
- If Danik won more games than Anton, print `Danik` (without quotes).
- If Anton and Danik won the same number of games, print `Friendship` (without quotes).

---

### 💡 Key Insights
1. **Single-pass counting:** The string length $n$ represents the outcomes of each game sequentially. A single traversal through the string is sufficient to accumulate individual win totals for both Anton (`'A'`) and Danik (`'D'`).
2. **Efficient I/O handling:** Since $n$ can be up to $100\,000$, using `BufferedReader` ensures fast reading compared to standard input operations.
3. **Decision logic:** Comparing the counts at the end directly dictates the output without any complex edge cases.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Anton and Danik (Codeforces 734A)
 * Language: Java 17
 */
public class AntonAndDanik {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String inputLine = reader.readLine();
        if (inputLine == null || inputLine.trim().isEmpty()) {
            return;
        }

        int n = Integer.parseInt(inputLine.trim());
        String s = reader.readLine().trim();

        int antonWins = 0;
        int danikWins = 0;

        // Count occurrences of 'A' and 'D'
        for (int i = 0; i < n; i++) {
            if (s.charAt(i) == 'A') {
                antonWins++;
            } else {
                danikWins++;
            }
        }

        // Determine overall winner
        if (antonWins > danikWins) {
            System.out.println("Anton");
        } else if (danikWins > antonWins) {
            System.out.println("Danik");
        } else {
            System.out.println("Friendship");
        }
    }
}
```
### 📊 Complexity Analysis

| Measure | Complexity | Detailed Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | We process each character of the outcome string $s$ of length $n$ exactly once. |
| **Space Complexity** | $\mathcal{O}(n)$ | Auxiliary space required to store the input string $s$ of length $n$ in memory. |
| **Best-Case Time** | $\Omega(n)$ | Even in the best case, all $n$ game outcomes must be read to determine the winner. |
| **Worst-Case Time** | $\mathcal{O}(n)$ | Traverses all $n$ characters for string inputs up to $100,000$ characters. |
