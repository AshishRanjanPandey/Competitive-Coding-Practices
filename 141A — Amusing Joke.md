# ⚡ Codeforces 141A — Amusing Joke

### 📝 Problem Description
So, the New Year holidays are over. Santa Claus and his colleagues can take a rest and have guests at last. When two "New Year and Christmas Men" meet, their assistants cut out of cardboard the letters from the guest's name and the host's name in honor of this event. Then they hung the letters above the main entrance. One night, when everyone went to bed, someone took all the letters of our characters' names. Then he may have shuffled the letters and put them in one pile in front of the door.

The next morning it was impossible to find the culprit who had made the disorder. But everybody wondered whether it is possible to restore the names of the host and his guests from the letters lying at the door? That is, we need to verify that there are no extra letters, and that nobody will need to cut more letters.

Help the "New Year and Christmas Men" and their friends to cope with this problem. You are given both inscriptions that hung over the front door the previous night, and a pile of letters that were found at the front door next morning.

**Input:**
- The input file consists of three lines:
  - The first line contains the guest's name.
  - The second line contains the name of the residence host.
  - The third line contains letters in a pile that were found at the door in the morning.
- All lines are non-empty and contain only uppercase Latin letters (`A`–`Z`). The length of each line does not exceed $100$.

**Output:**
- Print `"YES"` (without quotes) if the letters in the pile could be permuted to make the names of the "New Year and Christmas Men". Otherwise, print `"NO"` (without quotes).

---

### 💡 Key Insights
1. **Multiset Equality (Anagram Validation):**
   - The problem asks whether the multiset of characters in $\text{name}_1 + \text{name}_2$ is identical to the multiset of characters in $\text{pile}$.
   - Every character present in the combined names must appear in the pile with the exact same count, with no missing letters and no leftover letters.

2. **Quick Length Pruning:**
   - A necessary condition is that $|\text{name}_1| + |\text{name}_2| = |\text{pile}|$. If lengths differ, output `"NO"` immediately.

3. **Frequency Array vs. Sorting:**
   - **Approach 1 (Frequency Array):** Maintain an array of size $26$ for character counts. Increment frequencies for characters in $\text{name}_1$ and $\text{name}_2$, and decrement for characters in $\text{pile}$. If all counts reach $0$, the answer is `"YES"`.
   - **Approach 2 (Sorting):** Concatenate the first two strings, sort both character arrays, and verify equality with `Arrays.equals()`.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Amusing Joke (Codeforces 141A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class AmusingJoke {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));

        String guest = reader.readLine();
        String host = reader.readLine();
        String pile = reader.readLine();

        if (guest == null || host == null || pile == null) {
            return;
        }

        guest = guest.trim();
        host = host.trim();
        pile = pile.trim();

        // Step 1: Quick length verification
        if (guest.length() + host.length() != pile.length()) {
            System.out.println("NO");
            return;
        }

        // Step 2: Track letter frequencies (A-Z)
        int[] freq = new int[26];

        for (int i = 0; i < guest.length(); i++) {
            freq[guest.charAt(i) - 'A']++;
        }

        for (int i = 0; i < host.length(); i++) {
            freq[host.charAt(i) - 'A']++;
        }

        for (int i = 0; i < pile.length(); i++) {
            freq[pile.charAt(i) - 'A']--;
        }

        // Step 3: Check if all counts balanced out to 0
        for (int count : freq) {
            if (count != 0) {
                System.out.println("NO");
                return;
            }
        }

        System.out.println("YES");
    }
}
```
### 📊 Complexity Analysis

| Metric | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(L_1 + L_2 + L_3)$ | Single pass over each string to update the frequency array ($L_1, L_2, L_3 \le 100$), followed by a constant $26$-iteration loop. Total operations $\le 350$. |
| **Space Complexity (Auxiliary)** | $\mathcal{O}(1)$ | Fixed-size integer frequency array of length $26$ independent of input string lengths. |
| **Space Complexity (Input Parsing)** | $\mathcal{O}(L_1 + L_2 + L_3)$ | Memory allocated to store the three input strings read from `BufferedReader`. |
