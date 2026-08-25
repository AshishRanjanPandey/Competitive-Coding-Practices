# ⚡ Codeforces 520A — Pangram

### 📝 Problem Description
A word or a sentence in some language is called a **pangram** if all the characters of the alphabet of this language appear in it at least once. Pangrams are often used to demonstrate fonts in printing or test the output devices.

You are given a string consisting of lowercase and uppercase Latin letters. Check whether this string is a pangram. We say that the string contains a letter of the Latin alphabet if this letter occurs in the string in uppercase or lowercase.

**Input:**
- The first line contains a single integer $n$ ($1 \le n \le 100$) — the number of characters in the string.
- The second line contains the string consisting only of uppercase and lowercase Latin letters.

**Output:**
- Output `"YES"`, if the string is a pangram and `"NO"` otherwise.

---

### 💡 Key Insights
1. **Length Prerequisite:**
   - The English alphabet consists of $26$ distinct letters.
   - If the length of the string $n < 26$, it is impossible to contain all letters. We can immediately return `"NO"`.
2. **Case Insensitivity:**
   - Both lowercase and uppercase characters represent the same alphabet letter. Converting the entire string to lowercase (or uppercase) normalizes the characters for simple comparison.
3. **Unique Character Tracking:**
   - Use a `HashSet<Character>` or a boolean frequency array of size $26$ to keep track of every distinct letter present in the string.
   - If the count of unique Latin letters reaches exactly $26$, the answer is `"YES"`; otherwise, `"NO"`.
4. **Complexity:**
   - **Time Complexity:** $\mathcal{O}(n)$ — scanning the string of length at most $100$ runs well within the $2.0$-second time limit.
   - **Space Complexity:** $\mathcal{O}(1)$ — the auxiliary storage is bounded by the alphabet size ($26$ characters).

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.HashSet;
import java.util.Set;

/**
 * Problem: Pangram (Codeforces 520A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class Pangram {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String nLine = reader.readLine();
        if (nLine == null) {
            return;
        }
        
        int n = Integer.parseInt(nLine.trim());
        String s = reader.readLine();
        
        // A valid pangram must have at least 26 characters
        if (n < 26) {
            System.out.println("NO");
            return;
        }
        
        s = s.toLowerCase();
        Set<Character> uniqueLetters = new HashSet<>();
        
        for (int i = 0; i < n; i++) {
            uniqueLetters.add(s.charAt(i));
        }
        
        if (uniqueLetters.size() == 26) {
            System.out.println("YES");
        } else {
            System.out.println("NO");
        }
    }
}
```
---

### ⏱️ Complexity Analysis

| Metric | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | Iterating through the string of length $n$ once to insert characters into the set. |
| **Space Complexity** | $\mathcal{O}(1)$ | The `HashSet` stores at most $26$ unique Latin characters regardless of $n$. |
