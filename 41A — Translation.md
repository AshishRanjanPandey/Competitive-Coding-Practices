# 🚀 Codeforces 41A — Translation

### 📝 Problem Description
The translation from the Berland language into the Birland language is not an easy task. Those languages are very similar: a Berlandish word differs from a Birlandish word with the same meaning a little: it is spelled (and pronounced) reversely. For example, a Berlandish word `code` corresponds to a Birlandish word `edoc`. 

However, making a mistake during the "translation" is easy. Vasya translated the word $s$ from Berlandish into Birlandish as $t$. Help him: find out if he translated the word correctly.

**Input:**
- The first line contains word $s$, the second line contains word $t$.
- The words consist of lowercase Latin letters.
- The input data do not contain unnecessary spaces.
- The words are non-empty and their lengths do not exceed $100$ characters.

**Output:**
- If the word $t$ is a word $s$, written reversely, print `YES`.
- Otherwise, print `NO`.

---

### 💡 Key Insights
1. **String Reversal:** The problem requires checking if string $t$ is the exact reverse of string $s$.
2. **Built-in `StringBuilder`:** Java provides `StringBuilder.reverse()`, which flips a string in $O(N)$ time.
3. **Equivalence Check:** Comparing `new StringBuilder(s).reverse().toString()` with `t` using `.equals()` directly verifies if the translation is valid.
4. **Small Constraints:** With string lengths capped at $100$ characters, this reversal and equality check executes instantaneously.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Translation (Codeforces 41A)
 * Language: Java 17
 */
public class Translation {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));

        String s = reader.readLine();
        String t = reader.readLine();

        if (s == null || t == null) {
            return;
        }

        s = s.trim();
        t = t.trim();

        // Reverse string s using StringBuilder
        String reversedS = new StringBuilder(s).reverse().toString();

        // Check if the reversed version matches target string t
        if (reversedS.equals(t)) {
            System.out.println("YES");
        } else {
            System.out.println("NO");
        }
    }
}
```
| Complexity | Measure | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(N)$ | Reversing a string of length $N$ takes $O(N)$ operations, and comparing two strings of length $N$ takes $O(N)$ time. Since $N \le 100$, this executes in $< 1\text{ ms}$. |
| **Space Complexity** | $\mathcal{O}(N)$ | Additional space is used by `StringBuilder` to store the reversed string of length $N$. |
