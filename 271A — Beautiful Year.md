# 🚀 Codeforces 271A — Beautiful Year

### 📝 Problem Description
It seems like the year of 2013 came only yesterday. Do you know a curious fact? The year of 2013 is the first year after the old 1987 with only distinct digits.

Now you are suggested to solve the following problem: given a year number, find the minimum year number which is strictly larger than the given one and has only distinct digits.

**Input:**
- The single line contains integer $y$ ($1000 \le y \le 9000$) — the year number.

**Output:**
- Print a single integer — the minimum year number that is strictly larger than $y$ and all its digits are distinct. It is guaranteed that the answer exists.

---

### 💡 Key Insights
1. **Brute Force Approach:** Since the maximum year is bounded by small constraints ($1000 \le y \le 9000$), we can repeatedly increment $y$ by $1$ and check if its digits are distinct.
2. **Digit Extraction:** Extract the four individual digits (thousands, hundreds, tens, and units) using division and modulo operations.
3. **Uniqueness Check:** Compare all pairs of digits (`a != b`, `a != c`, `a != d`, `b != c`, `b != d`, `c != d`).
4. **Guaranteed Termination:** The loop will check at most a few dozen numbers before finding the next beautiful year, operating in $O(1)$ time complexity.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Beautiful Year (Codeforces 271A)
 * Language: Java 17
 */
public class BeautifulYear {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String input = reader.readLine();
        if (input == null) {
            return;
        }
        
        int year = Integer.parseInt(input.trim());
        
        while (true) {
            year++;
            if (hasDistinctDigits(year)) {
                System.out.println(year);
                break;
            }
        }
    }

    /**
     * Helper function to check if all digits of a 4-digit year are distinct.
     */
    private static boolean hasDistinctDigits(int year) {
        int a = year / 1000;
        int b = (year / 100) % 10;
        int c = (year / 10) % 10;
        int d = year % 10;

        return a != b && a != c && a != d && b != c && b != d && c != d;
    }
}
```
### 📊 Complexity Analysis

| Complexity | Parameter | Value | Explanation |
| :--- | :--- | :--- | :--- |
| **Time Complexity** | $O(1)$ | $\approx 200$ ops | The maximum gap between two consecutive "beautiful years" in the given range is less than 100 increments. Checking digits takes $O(1)$ constant steps. |
| **Space Complexity** | $O(1)$ | $O(1)$ | Only a few integer variables (`a`, `b`, `c`, `d`, `year`) are used to store digit values and input state. |
