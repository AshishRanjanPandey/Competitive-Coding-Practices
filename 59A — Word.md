# 🚀 Codeforces 59A — Word

### 📝 Problem Description
Vasya is very upset that many people on the Net mix uppercase and lowercase letters in one word. That's why he decided to invent an extension for his favorite browser that would change the letters' register in every word so that it either only consisted of lowercase letters or, vice versa, only of uppercase ones. 

At that, as little as possible letters should be changed in the word. For example, the word `HoUse` must be replaced with `house`, and the word `ViP` — with `VIP`. If a word contains an equal number of uppercase and lowercase letters, you should replace all the letters with lowercase ones. For example, `maTRIx` should be replaced by `matrix`.

**Input:**
The first line contains a word $s$ — it consists of uppercase and lowercase Latin letters and possesses a length from $1$ to $100$.

**Output:**
Print the corrected word $s$. If the given word $s$ has strictly more uppercase letters, make the word written in the uppercase register, otherwise — in the lowercase one.

---

### 💡 Key Insights
1. **Case Frequency Counting:** Iterate through the string character by character to count the number of uppercase and lowercase letters.
2. **Decision Rule:**
   * If $\text{Uppercase Count} > \text{Lowercase Count}$, convert the entire string to **UPPERCASE**.
   * If $\text{Uppercase Count} \le \text{Lowercase Count}$ (including the equal case), convert the entire string to **lowercase**.
3. **Built-in String Utilities:** Java's `Character.isUpperCase()` makes character classification clean, while `String.toUpperCase()` and `String.toLowerCase()` perform the full transformation efficiently.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Word (Codeforces 59A)
 * Language: Java 17
 */
public class Word {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.next();
        sc.close();

        int upperCount = 0;
        int lowerCount = 0;

        // Count uppercase and lowercase characters
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if (Character.isUpperCase(ch)) {
                upperCount++;
            } else {
                lowerCount++;
            }
        }

        // Apply transformation rule
        if (upperCount > lowerCount) {
            System.out.println(s.toUpperCase());
        } else {
            System.out.println(s.toLowerCase());
        }
    }
}
```
### 📊 Complexity Analysis

| Type | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | We iterate through the string of length $n$ once to count letter cases and once more during transformation. Since $n \le 100$, this executes almost instantaneously. |
| **Space Complexity** | $\mathcal{O}(1)$ | Auxiliary space is constant as we only store integer counters and references to standard input/output. |
