# 🚀 Codeforces 131A — cAPS lOCK

### 📝 Problem Description
Caps lock is a computer keyboard key. Pressing it sets an input mode in which typed letters are capital by default. If it is pressed by accident, it leads to accidents like typing with inverted or unexpected capitalization.

Let's consider that a word has been typed with the Caps Lock key accidentally switched on, if:
- either it only contains uppercase letters;
- or all letters except for the first one are uppercase.

In this case, we should automatically change the case of all letters (uppercase letters become lowercase, and lowercase letters become uppercase). For example, the case of the letters forming words `"cAPS"`, `"HTTP"`, `"z"` should be inverted to `"Caps"`, `"http"`, `"Z"`.

If neither of the rules applies, the program should leave the word unchanged.

**Input:**
- The first line contains a single word consisting of uppercase and lowercase Latin letters. The word's length is from $1$ to $100$ characters, inclusive.

**Output:**
- Print the result of the given word's processing.

---

### 💡 Key Insights
1. **Unifying the Condition:** Both target cases require that **every letter from index $1$ to the end is uppercase**. The first letter at index $0$ can be either uppercase or lowercase.
2. **Single-Character Edge Case:** Words of length $1$ (like `"a"` or `"A"`) vacuously satisfy the condition because there are no letters after index $0$, meaning their case should always be inverted.
3. **Inversion Logic:** If the condition holds, iterate through the string and flip the casing of every character using `Character.isUpperCase(c)` and its corresponding helper methods; otherwise, output the original string as is.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: cAPS lOCK (Codeforces 131A)
 * Language: Java 17
 */
public class CapsLock {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String word = reader.readLine();
        if (word == null || word.isEmpty()) {
            return;
        }

        // Check if all characters from index 1 to the end are uppercase
        boolean shouldInvert = true;
        for (int i = 1; i < word.length(); i++) {
            if (Character.isLowerCase(word.charAt(i))) {
                shouldInvert = false;
                break;
            }
        }

        if (shouldInvert) {
            StringBuilder sb = new StringBuilder(word.length());
            for (int i = 0; i < word.length(); i++) {
                char ch = word.charAt(i);
                if (Character.isUpperCase(ch)) {
                    sb.append(Character.toLowerCase(ch));
                } else {
                    sb.append(Character.toUpperCase(ch));
                }
            }
            System.out.println(sb.toString());
        } else {
            System.out.println(word);
        }
    }
}
```
| Metric | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(|s|)$ | One pass to validate characters from index $1$ onwards and a second pass to flip the cases. Since $\|s\| \le 100$, operations take $\le 200$ steps and run well under $1\text{ ms}$. |
| **Auxiliary Space** | $\mathcal{O}(|s|)$ | Requires a `StringBuilder` buffer of size $|s|$ to accumulate the inverted output string. |
| **Worst-case Scenarios** | $\mathcal{O}(|s|)$ | Words like `"cAPS"` or `"HTTP"` trigger the full transformation pass. |
| **Best-case Scenarios** | $\mathcal{O}(1)$ | Words where the second character is already lowercase (e.g., `"Lock"`) trigger an immediate loop exit during validation. |
