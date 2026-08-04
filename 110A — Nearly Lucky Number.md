# 🚀 Codeforces 110A — Nearly Lucky Number

### 📝 Problem Description
Petya loves lucky numbers. We all know that lucky numbers are the positive integers whose decimal representations contain only the lucky digits `4` and `7`. For example, numbers `47`, `744`, `4` are lucky and `5`, `17`, `467` are not.

Unfortunately, not all numbers are lucky. Petya calls a number **nearly lucky** if the number of lucky digits in it is a lucky number. He wonders whether number $n$ is a nearly lucky number.

**Input:**
The only line contains an integer $n$ ($1 \le n \le 10^{18}$).

**Output:**
Print on a single line `YES` if $n$ is a nearly lucky number. Otherwise, print `NO` (without quotes).

---

### 💡 Key Insights
1. **String representation for large constraints:** Since $n \le 10^{18}$, reading the input directly as a `String` allows processing up to 19 digits cleanly without integer overflow concerns or modulo loop overhead.
2. **Two-phase condition:** 
   - First, count total occurrences of the digits `'4'` and `'7'` in $n$.
   - Second, check if that total count itself consists *only* of lucky digits (`4` or `7`).
3. **Small search space:** Because $n$ has at most 19 digits, the count of lucky digits can only range from $0$ to $19$. The only valid lucky counts within this domain are `4` and `7`.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Nearly Lucky Number (Codeforces 110A)
 * Language: Java 17
 */
public class NearlyLuckyNumber {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        if (!sc.hasNext()) {
            return;
        }

        // Read input as a string to easily handle values up to 10^18
        String n = sc.next();
        sc.close();

        int luckyDigitCount = 0;

        // Count occurrences of '4' and '7'
        for (int i = 0; i < n.length(); i++) {
            char ch = n.charAt(i);
            if (ch == '4' || ch == '7') {
                luckyDigitCount++;
            }
        }

        // A number is nearly lucky if the total count of lucky digits is itself a lucky number
        if (isLucky(luckyDigitCount)) {
            System.out.println("YES");
        } else {
            System.out.println("NO");
        }
    }

    /**
     * Helper method to verify if a given integer consists exclusively of lucky digits ('4' and '7').
     */
    private static boolean isLucky(int count) {
        if (count == 0) {
            return false;
        }

        while (count > 0) {
            int digit = count % 10;
            if (digit != 4 && digit != 7) {
                return false;
            }
            count /= 10;
        }

        return true;
    }
}
```
### 📊 Complexity Analysis

| Type | Complexity | Description |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(\log_{10} n)$ | We iterate through all digits of $n$. For $n \le 10^{18}$, there are at most 19 digits, making it essentially $\mathcal{O}(1)$ constant time. |
| **Space Complexity** | $\mathcal{O}(\log_{10} n)$ | Auxiliary space required to store $n$ as a string of up to 19 characters, which operates in $\mathcal{O}(1)$ space. |
