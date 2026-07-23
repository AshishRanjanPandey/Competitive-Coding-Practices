# 🚀 Codeforces 112A — Petya and Strings

### 📝 Problem Description
Little Petya loves presents. His mum bought him two strings of the same size for his birthday. The strings consist of uppercase and lowercase Latin letters. Now Petya wants to compare those two strings lexicographically. The letters' case does not matter, that is, an uppercase letter is considered equivalent to the corresponding lowercase letter. Help Petya perform the comparison.

**Input:**
Each of the first two lines contains a bought string. The strings' lengths range from $1$ to $100$ inclusive. It is guaranteed that the strings are of the same length and consist of uppercase and lowercase Latin letters.

**Output:**
* Print `-1` if the first string is less than the second one.
* Print `1` if the second string is less than the first one.
* Print `0` if the strings are equal.

---

### 💡 Key Insights
1. **Case Insensitivity:** Since uppercase and lowercase letters are treated equally, convert both input strings completely to lowercase (or uppercase) before comparing.
2. **Built-in String Comparison:** Java's `String.compareTo()` method performs lexicographical comparisons based on ASCII values.
   * If `a.compareTo(b) < 0`, `a` comes before `b`.
   * If `a.compareTo(b) > 0`, `a` comes after `b`.
   * If `a.compareTo(b) == 0`, both strings are identical.
3. **Small Constraints:** The string length $L \le 100$ is extremely small, so standard linear string comparison runs virtually instantly well within the 2.0-second time limit.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Petya and Strings (Codeforces 112A)
 * Language: Java 17
 */
public class PetyaAndStrings {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Read and normalize both strings to lowercase
        String s1 = sc.next().toLowerCase();
        String s2 = sc.next().toLowerCase();

        // Lexicographical comparison
        int comparison = s1.compareTo(s2);

        if (comparison < 0) {
            System.out.println("-1");
        } else if (comparison > 0) {
            System.out.println("1");
        } else {
            System.out.println("0");
        }

        sc.close();
    }
}
```
### ⏱️ Complexity
* **Time Complexity:** $\mathcal{O}(N)$ — where $N$ is the length of the strings ($1 \le N \le 100$). Lowercasing and comparing two strings of length $N$ takes linear time relative to the number of characters.
* **Space Complexity:** $\mathcal{O}(N)$ — required to store the normalized lowercase strings in memory.
