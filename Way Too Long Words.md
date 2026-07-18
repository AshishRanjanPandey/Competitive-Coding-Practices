# 🚀 Codeforces 71A — Way Too Long Words

### 📝 Problem Description
Sometimes some words like "localization" or "internationalization" are so long that writing them many times in one text is quite tiresome.

Let's consider a word too long, if its length is **strictly more than 10 characters**. All too long words should be replaced with a special abbreviation.

This abbreviation is made like this: we write down the first and the last letter of a word and between them we write the number of letters between the first and the last letters. That number is in decimal system and doesn't contain any leading zeroes.

* Thus, `"localization"` will be spelt as `"l10n"`.
* `"internationalization"` will be spelt as `"i18n"`.

---

### 💻 Java Solution

```java
import java.util.Scanner;
 
/**
 * Problem: Way Too Long Words (Codeforces 71A)
 * Language: Java 17
 */
public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Read the number of words
        if (scanner.hasNextInt()) {
            int n = scanner.nextInt();
            // Consume the remaining newline character after nextInt()
            scanner.nextLine(); 
            
            // Process each word
            for (int i = 0; i < n; i++) {
                String word = scanner.nextLine();
                int length = word.length();
                
                // Check if the word length is strictly more than 10
                if (length > 10) {
                    // Abbreviation: first letter + (length - 2) + last letter
                    String abbreviation = "" + word.charAt(0) + (length - 2) + word.charAt(length - 1);
                    System.out.println(abbreviation);
                } else {
                    // Print the word as it is
                    System.out.println(word);
                }
            }
        }
        
        scanner.close();
    }
}
```
| Metric | Complexity | Description |
| :--- | :---: | :--- |
| **Time Complexity** | $\mathcal{O}(n \times L)$ | **Linear Time.** We loop through all $n$ words exactly once. Inside the loop, checking the length and accessing characters takes $\mathcal{O}(1)$ time, while reading each string scales with its length $L$. |
| **Space Complexity** | $\mathcal{O}(L)$ | **Linear Space.** The program handles one word of length $L$ at a time in memory, overwriting it in the next iteration rather than accumulating space. |
