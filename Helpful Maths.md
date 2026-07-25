# 🚀 Codeforces 339A — Helpful Maths

### 📝 Problem Description
Xenia the beginner mathematician is a third year student at elementary school. She is now learning the addition operation.

The teacher has written down the sum of multiple numbers. Pupils should calculate the sum. To make the calculation easier, the sum only contains numbers 1, 2 and 3. Still, that isn't enough for Xenia. She is only beginning to count, so she can calculate a sum only if the summands follow in non-decreasing order. For example, she can't calculate sum 1+3+2+1 but she can calculate sums 1+1+2 and 3+3.

You've got the sum that was written on the board. Rearrange the summands and print the sum in such a way that Xenia can calculate the sum.

**Input:**
The first line contains a non-empty string `s` — the sum Xenia needs to count. String `s` contains no spaces. It only contains digits and characters `"+"`. Besides, string `s` is a correct sum of numbers 1, 2 and 3. String `s` is at most 100 characters long.

**Output:**
Print the new sum that Xenia can count.

---

### 💡 Key Insights
1. **Splitting Summands:** The input string consists of digits (`1`, `2`, `3`) separated by `+` characters. We can split the string by `+` to isolate individual numbers.
2. **Sorting for Non-Decreasing Order:** To satisfy Xenia's condition, the numbers must appear in ascending order. Sorting the list/array of numbers arranges them in non-decreasing order.
3. **Reconstructing the Expression:** After sorting, we join the sorted numbers back together with `+` signs.
4. **Efficiency:** Since the input string length $N \le 100$, splitting, sorting, and joining take $\mathcal{O}(N \log N)$ time and $\mathcal{O}(N)$ space, which easily runs within the time limit.

---

### 💻 Java Solution

```java
import java.util.Arrays;
import java.util.Scanner;

/**
 * Problem: Helpful Maths (Codeforces 339A)
 * Language: Java 17
 */
public class HelpfulMaths {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.next();
        sc.close();

        // Split the string by '+' (escaped as '\\+' in regex)
        String[] numbers = s.split("\\+");

        // Sort the numbers in non-decreasing order
        Arrays.sort(numbers);

        // Reconstruct and print the new sum
        System.out.println(String.join("+", numbers));
    }
}
```
---

### ⏱️ Complexity Analysis

| Metric | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(N \log N)$ | Splitting and joining takes $\mathcal{O}(N)$ time. Sorting array of length $K$ (where $K \le N$) takes $\mathcal{O}(K \log K) \subseteq \mathcal{O}(N \log N)$ time. |
| **Space Complexity** | $\mathcal{O}(N)$ | Auxiliary space required to store the split string elements in an array. |

> **Note:** Since the string length $N \le 100$, $N \log N \approx 660$ operations, which executes almost instantaneously ($\approx 0\text{ ms}$).
