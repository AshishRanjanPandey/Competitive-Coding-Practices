# 🚀 Codeforces 236A — Boy or Girl

### 📝 Problem Description
Those days, many boys use beautiful girls' photos as avatars in forums. So it is pretty hard to tell the gender of a user at the first glance. Last year, our hero went to a forum and had a nice chat with a beauty (he thought so). After that they talked very often and eventually they became a couple in the network.

But yesterday, he came to see "her" in the real world and found out "she" is actually a very strong man! Our hero is very sad and he is too tired to love again now. So he came up with a way to recognize users' genders by their user names.

This is his method: if the number of distinct characters in one's user name is odd, then he is a male, otherwise she is a female. You are given the string that denotes the user name, please help our hero to determine the gender of this user by his method.

**Input:**
The first line contains a non-empty string, that contains only lowercase English letters — the user name. This string contains at most 100 letters.

**Output:**
* Print `CHAT WITH HER!` if the user is female according to our hero's method.
* Print `IGNORE HIM!` if the user is male.

---

### 💡 Key Insights
1. **Distinct Character Count:** The core of the problem requires counting unique characters in the string while ignoring duplicates.
2. **Using a Set:** A `HashSet` naturally enforces uniqueness. By inserting every character of the string into a set, duplicate characters are ignored, and the set's size gives the exact count of unique letters.
3. **Parity Check:** 
   * If `set.size() % 2 == 0` (even), print `CHAT WITH HER!`.
   * If `set.size() % 2 != 0` (odd), print `IGNORE HIM!`.
4. **Efficiency:** Since the input length $L \le 100$ and consists only of lowercase English alphabet characters (at most 26 unique characters), operations on the set run in $\mathcal{O}(1)$ auxiliary space and $\mathcal{O}(N)$ time.

---

### 💻 Java Solution

```java
import java.util.Scanner;
import java.util.HashSet;
import java.util.Set;

/**
 * Problem: Boy or Girl (Codeforces 236A)
 * Language: Java 17
 */
public class BoyOrGirl {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String username = sc.next();

        // Use a Set to store distinct characters
        Set<Character> distinctChars = new HashSet<>();

        for (char c : username.toCharArray()) {
            distinctChars.add(c);
        }

        // If the number of distinct characters is even -> female
        // Otherwise -> male
        if (distinctChars.size() % 2 == 0) {
            System.out.println("CHAT WITH HER!");
        } else {
            System.out.println("IGNORE HIM!");
        }

        sc.close();
    }
}
```
---

### ⏱️ Complexity Analysis

| Type | Complexity | Description |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(N)$ | We iterate through the string of length $N$ once to insert characters into the set. Set operations (insert and size lookup) run in $\mathcal{O}(1)$ time. |
| **Space Complexity** | $\mathcal{O}(1)$ | Since the input consists only of lowercase English letters, the set stores at most $26$ unique elements regardless of string length $N$. |
