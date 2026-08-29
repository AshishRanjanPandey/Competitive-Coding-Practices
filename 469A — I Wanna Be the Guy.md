# ⚡ Codeforces 469A — I Wanna Be the Guy

### 📝 Problem Description
There is a game called "I Wanna Be the Guy", consisting of $n$ levels. Little X and his friend Little Y are addicted to the game. Each of them wants to pass the whole game.

Little X can pass only $p$ levels of the game. Little Y can pass only $q$ levels of the game. You are given the indices of levels Little X can pass and the indices of levels Little Y can pass. Will Little X and Little Y pass the whole game, if they cooperate with each other?

**Input:**
- The first line contains a single integer $n$ ($1 \le n \le 100$) — the total number of levels in the game.
- The second line contains an integer $p$ ($0 \le p \le n$), followed by $p$ distinct integers $a_1, a_2, \dots, a_p$ ($1 \le a_i \le n$) — the indices of levels Little X can pass.
- The third line contains an integer $q$ ($0 \le q \le n$), followed by $q$ distinct integers $b_1, b_2, \dots, b_q$ ($1 \le b_i \le n$) — the indices of levels Little Y can pass.

**Output:**
- If they can pass all levels from $1$ to $n$ together, print `"I become the guy."`
- Otherwise, print `"Oh, my keyboard!"`

---

### 💡 Key Insights
1. **Set Union Property:**
   - Little X and Little Y cooperate, meaning a level is considered passed if **either** Little X or Little Y (or both) can pass it.
   - We need to check whether the union of their passed levels contains all integers from $1$ to $n$.

2. **Efficient Tracking:**
   - Using a hash set (`HashSet<Integer>` in Java) automatically handles duplicates.
   - Insert all $p$ level indices from Little X and all $q$ level indices from Little Y into the set.
   - Since all level indices are guaranteed to be in the range $[1, n]$, the friends can pass the whole game if and only if the size of the set equals $n$.

3. **Complexity:**
   - **Time Complexity:** $\mathcal{O}(p + q) \le \mathcal{O}(n)$ — reading the input and inserting into the hash set takes constant time per element.
   - **Space Complexity:** $\mathcal{O}(n)$ — to store up to $n$ unique level indices.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.HashSet;
import java.util.Set;
import java.util.StringTokenizer;

/**
 * Problem: I Wanna Be the Guy (Codeforces 469A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class IWannaBeTheGuy {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String nLine = reader.readLine();
        if (nLine == null) {
            return;
        }
        
        int n = Integer.parseInt(nLine.trim());
        Set<Integer> passedLevels = new HashSet<>();
        
        // Read levels Little X can pass
        StringTokenizer stX = new StringTokenizer(reader.readLine());
        int p = Integer.parseInt(stX.nextToken());
        for (int i = 0; i < p; i++) {
            passedLevels.add(Integer.parseInt(stX.nextToken()));
        }
        
        // Read levels Little Y can pass
        StringTokenizer stY = new StringTokenizer(reader.readLine());
        int q = Integer.parseInt(stY.nextToken());
        for (int i = 0; i < q; i++) {
            passedLevels.add(Integer.parseInt(stY.nextToken()));
        }
        
        // If the number of unique passed levels equals n, they beat the game
        if (passedLevels.size() == n) {
            System.out.println("I become the guy.");
        } else {
            System.out.println("Oh, my keyboard!");
        }
    }
}
```
### 📊 Complexity Analysis

| Metric | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(p + q) \approx \mathcal{O}(n)$ | Inserting $p$ and $q$ elements into a `HashSet` takes $\mathcal{O}(1)$ average time per element, totaling at most $2n$ operations. |
| **Space Complexity** | $\mathcal{O}(n)$ | The `HashSet` stores at most $n$ unique level integers (from $1$ to $n$). |
