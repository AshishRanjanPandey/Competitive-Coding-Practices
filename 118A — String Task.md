# 🚀 Codeforces 118A — String Task

### 📝 Problem Description
Petya started to attend programming lessons. On the first lesson his task was to write a simple program. The program was supposed to do the following: in the given string, consisting of uppercase and lowercase Latin letters, it:
1. Deletes all the vowels,
2. Inserts a character `.` before each consonant,
3. Replaces all uppercase consonants with corresponding lowercase ones.

Vowels are letters `"A"`, `"O"`, `"Y"`, `"E"`, `"U"`, `"I"`, and the rest are consonants. The program's input is exactly one string, it should return the output as a single string, resulting after processing the initial string.

**Input:**
The first line represents the input string of Petya's program. This string only consists of uppercase and lowercase Latin letters and its length is from $1$ to $100$, inclusive.

**Output:**
Print the resulting string. It is guaranteed that this string is not empty.

---

### 💡 Key Insights
1. **Case Normalization First:** Converting the entire string to lowercase at the very start handles the requirement of replacing uppercase consonants with lowercase ones and simplifies vowel checks.
2. **Vowel Set Definition:** The problem explicitly considers `'a'`, `'o'`, `'y'`, `'e'`, `'u'`, and `'i'` as vowels. Note that **'y'** is treated as a vowel here.
3. **String Construction:** Using `StringBuilder` allows efficient $O(1)$ amortized appending for each valid consonant along with its preceding `.` prefix.
4. **Time & Space Complexity:** With string length $N \le 100$, an $O(N)$ linear scan easily processes within time limits using minimal $O(N)$ extra memory.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: String Task (Codeforces 118A)
 * Language: Java 17
 */
public class StringTask {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.next().toLowerCase(); // Convert to lowercase immediately
        sc.close();
        
        StringBuilder result = new StringBuilder();
        
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            // Skip if the character is a vowel (including 'y')
            if (ch == 'a' || ch == 'o' || ch == 'y' || ch == 'e' || ch == 'u' || ch == 'i') {
                continue;
            } else {
                result.append('.').append(ch);
            }
        }
        
        System.out.println(result.toString());
    }
}
```
### ⏱️ Complexity Analysis

| Resource | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(N)$ | We iterate through the string of length $N$ exactly once. Each character check and `StringBuilder` append operation runs in $\mathcal{O}(1)$ constant time. |
| **Space Complexity** | $\mathcal{O}(N)$ | `StringBuilder` stores at most $2N$ characters (each consonant gets a `.` prefix), which simplifies to $\mathcal{O}(N)$ auxiliary space. |
