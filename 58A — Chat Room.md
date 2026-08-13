# 🚀 Codeforces 58A — Chat Room

### 📝 Problem Description
Vasya has recently learned to type and log on to the Internet. He immediately entered a chat room and decided to say hello to everybody. Vasya typed the word $s$. 

It is considered that Vasya managed to say hello if several letters can be deleted from the typed word so that it resulted in the word `"hello"`. Determine whether Vasya managed to say hello by the given word $s$.

**Input:**
- The first and only line contains the word $s$, which Vasya typed ($1 \le |s| \le 100$). The word consists of lowercase Latin letters.

**Output:**
- If Vasya managed to say hello, print `"YES"`, otherwise print `"NO"`.

---

### 💡 Key Insights
1. **Subsequence Matching:** The problem asks whether the word `"hello"` appears as a **subsequence** in the input string $s$. The target characters (`h`, `e`, `l`, `l`, `o`) must appear in that precise order, but other characters can be present in between.
2. **Two-Pointer Approach:** Maintain an index pointing to the character we are looking for in `"hello"`. Iterate through string $s$: whenever the current character matches our target character, advance our target pointer.
3. **Time & Space Efficiency:** A single linear scan through the string takes $O(|s|)$ time using $O(1)$ auxiliary space.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Chat room (Codeforces 58A)
 * Language: Java 17
 */
public class ChatRoom {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String s = reader.readLine();
        if (s == null || s.trim().isEmpty()) {
            return;
        }
        
        s = s.trim();
        String target = "hello";
        int targetIdx = 0;
        
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == target.charAt(targetIdx)) {
                targetIdx++;
            }
            // Early exit if all characters of "hello" have been matched
            if (targetIdx == target.length()) {
                break;
            }
        }
        
        if (targetIdx == target.length()) {
            System.out.println("YES");
        } else {
            System.out.println("NO");
        }
    }
}
```
### 📊 Complexity Analysis

| Complexity | Measure | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $O(N)$ | We perform a single linear scan through the string $s$ of length $N$ ($N \le 100$). |
| **Space Complexity** | $O(1)$ | Uses a constant amount of auxiliary memory for pointers and fixed variables. |

---
