# 🚀 Codeforces 1030A — In Search of an Easy Problem

### 📝 Problem Description
When preparing a tournament, Codeforces coordinators try their best to make the first problem as easy as possible. This time the coordinator had chosen some problem and asked $n$ people about their opinions. Each person answered whether this problem is easy or hard.

If at least one of these $n$ people has answered that the problem is hard, the coordinator decides to change the problem. For the given responses, check if the problem is easy enough.

**Input:**
- The first line contains a single integer $n$ ($1 \le n \le 100$) — the number of people who were asked to give their opinions.
- The second line contains $n$ integers, each integer is either $0$ or $1$. If the $i$-th integer is $0$, then the $i$-th person thinks that the problem is easy; if it is $1$, then the $i$-th person thinks that the problem is hard.

**Output:**
- Print one word: `"EASY"` if the problem is easy according to all responses, or `"HARD"` if there is at least one person who thinks the problem is hard. You may print every letter in any register.

---

### 💡 Key Insights
1. **Condition Check:** The core condition is simple: if the array of opinions contains at least one `1`, the answer is `"HARD"`. Otherwise, if all elements are `0`, the answer is `"EASY"`.
2. **Early Exit / Flag:** As we iterate through the given responses, we can set a boolean flag to `true` whenever we encounter a `1`. 
3. **Time & Space Efficiency:** Reading the inputs sequentially takes $O(n)$ time using $O(1)$ auxiliary space, well within the strict time limits of Codeforces.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: In Search of an Easy Problem (Codeforces 1030A)
 * Language: Java 17
 */
public class InSearchOfAnEasyProblem {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String line = reader.readLine();
        if (line == null) {
            return;
        }
        
        int n = Integer.parseInt(line.trim());
        StringTokenizer st = new StringTokenizer(reader.readLine());
        
        boolean isHard = false;
        
        for (int i = 0; i < n; i++) {
            int opinion = Integer.parseInt(st.nextToken());
            // If even a single person thinks the problem is hard, mark as hard
            if (opinion == 1) {
                isHard = true;
                break; // Early exit since one '1' is sufficient to decide
            }
        }
        
        if (isHard) {
            System.out.println("HARD");
        } else {
            System.out.println("EASY");
        }
    }
}
```
### 📊 Complexity Analysis

| Type | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | We iterate through the $n$ inputs at most once (or terminate early on encountering `1`). |
| **Space Complexity** | $\mathcal{O}(1)$ | Only scalar primitive variables (`n`, `isHard`, `opinion`) are used without allocating additional memory. |
