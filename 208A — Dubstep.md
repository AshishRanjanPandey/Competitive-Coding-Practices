# ⚡ Codeforces 208A — Dubstep

### 📝 Problem Description
Vasya works as a DJ in the best Berland nightclub, and he often uses dubstep music in his performance. Recently, he has decided to take a couple of old songs and make dubstep remixes from them.

Let's assume that a song consists of some number of words. To make the dubstep remix of this song, Vasya inserts a certain number of words `"WUB"` before the first word of the song (the number may be zero), after the last word (the number may be zero), and between words (at least one between any pair of neighbouring words), and then the boy glues together all the words, including `"WUB"`, in one string and plays the song at the club.

For example, a song with words `"I AM X"` can transform into a dubstep remix as `"WUBWUBIWUBAMWUBWUBX"` and cannot transform into `"WUBWUBIAMWUBX"`.

Recently, Petya has heard Vasya's new dubstep track, but since he isn't into modern music, he decided to find out what was the initial song that Vasya remixed. Help Petya restore the original song.

**Input:**
- The input consists of a single non-empty string, consisting only of uppercase English letters.
- The string's length does not exceed $200$ characters.
- It is guaranteed that before Vasya remixed the song, no word contained the substring `"WUB"` in it.
- Vasya didn't change the word order.
- It is guaranteed that initially the song had at least one word.

**Output:**
- Print the words of the initial song that Vasya used to make a dubstep remix. Separate the words with a single space.

---

### 💡 Key Insights
1. **Separation by Marker String:**
   - The token `"WUB"` serves strictly as padding and a separator between original words.
   - Any single or consecutive group of `"WUB"` tokens between words acts as a word boundary.
   - Any `"WUB"` tokens appearing at the extreme start (prefix) or extreme end (suffix) of the string represent leading or trailing noise and should be removed entirely.

2. **Parsing Strategies:**
   - **Regex / Built-in String Manipulation:**
     - Replace every instance of `"WUB"` with a space character: `" "`
     - Condense any runs of multiple spaces into a single space.
     - Trim leading and trailing spaces.
   - **Linear Scanning (Pointer / State-Machine):**
     - Iterate through the string from left to right.
     - Check if the current 3-character slice equals `"WUB"`.
     - If it matches, advance the index by $3$. If preceded by actual word characters, record that a space boundary is pending.
     - If it does not match, append the character to the current word (printing a separating space beforehand if a word boundary was previously encountered) and advance by $1$.

3. **Constraints & Efficiency:**
   - The string length $|S| \le 200$, which is very small. Both string replacement techniques and linear scans run virtually instantaneously ($\le 1\text{ ms}$).

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Dubstep (Codeforces 208A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class Dubstep {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        String s = reader.readLine();
        if (s == null || s.isEmpty()) {
            return;
        }

        StringBuilder result = new StringBuilder();
        int n = s.length();
        int i = 0;
        boolean spaceNeeded = false;

        while (i < n) {
            // Check if current 3-character window matches "WUB"
            if (i + 2 < n && s.charAt(i) == 'W' && s.charAt(i + 1) == 'U' && s.charAt(i + 2) == 'B') {
                i += 3;
                // A word has already been printed, so a space is needed before the next word
                if (result.length() > 0) {
                    spaceNeeded = true;
                }
            } else {
                if (spaceNeeded) {
                    result.append(' ');
                    spaceNeeded = false;
                }
                result.append(s.charAt(i));
                i++;
            }
        }

        System.out.println(result);
    }
}
```

---

### ⏱️ Complexity Analysis

| Metric | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(|S|)$ | Single linear traversal through the string of length $|S| \le 200$. |
| **Space Complexity (Auxiliary)** | $\mathcal{O}(1)$ | Uses a constant number of control variables (`i`, `n`, `spaceNeeded`). |
| **Space Complexity (Output)** | $\mathcal{O}(|S|)$ | Allocates a `StringBuilder` that holds at most $|S|$ characters to output the reconstructed song. |
