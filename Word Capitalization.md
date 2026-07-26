# 🚀 Codeforces 281A — Word Capitalization

### 📝 Problem Description
Capitalization is writing a word with its first letter as a capital letter. Your task is to capitalize the given word.

Note, that during capitalization all the letters except the first one remain unchanged.

**Input:**
A single line contains a non-empty word. This word consists of lowercase and uppercase English letters. The length of the word will not exceed 10^3.

**Output:**
Output the given word after capitalization.

---

### 💡 Key Insights
1. **Targeted Transformation:** Only the very first character at index `0` needs to be converted to uppercase using standard library functions (`Character.toUpperCase` in Java).
2. **Preserving Casing:** All remaining characters from index `1` to the end of the string must stay exactly as they were provided in the input, regardless of whether they are uppercase or lowercase.
3. **Substring Operations:** We can achieve this by concatenating the capitalized first character with the rest of the string obtained via `word.substring(1)`.
4. **Efficiency:** Since the word length $N \le 10^3$, extracting the first character and taking a substring takes $\mathcal{O}(N)$ time and $\mathcal{O}(N)$ space, running instantaneously within the time limit.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Word Capitalization (Codeforces 281A)
 * Language: Java 17
 */
public class WordCapitalization {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String word = sc.next();
        sc.close();

        // Capitalize the first character and append the remaining substring
        String result = Character.toUpperCase(word.charAt(0)) + word.substring(1);

        // Print the capitalized word
        System.out.println(result);
    }
}
```
### ⏱️ Complexity Analysis

| Resource | Complexity | Description |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(N)$ | Accessing the first character, converting it to uppercase, and taking a substring takes linear time relative to the length of the string $N$. |
| **Space Complexity** | $\mathcal{O}(N)$ | A new string of length $N$ is created to store the final capitalized result. |
