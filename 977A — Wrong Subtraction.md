# 🚀 Codeforces 977A — Wrong Subtraction

### 📝 Problem Description
Little girl Tanya is learning how to decrease a number by one, but she does it wrong with a number consisting of two or more digits. Tanya subtracts one from a number by the following algorithm:
- If the last digit of the number is non-zero, she decreases the number by one;
- If the last digit of the number is zero, she divides the number by 10 (i.e. removes the last digit).

You are given an integer number $n$. Tanya will subtract one from it $k$ times. Your task is to print the result after all $k$ subtractions.

**Input:**
The first line of the input contains two integer numbers $n$ and $k$ ($2 \le n \le 10^9$, $1 \le k \le 50$) — the number from which Tanya will subtract and the number of subtractions correspondingly.

**Output:**
Print one integer number — the result of decreasing $n$ by one $k$ times.

---

### 💡 Key Insights
1. **Algorithmic Simulation:** Since $k$ is small ($1 \le k \le 50$), simulating Tanya's subtraction rule step-by-step using a loop running $k$ times completes well within time limits.
2. **Modulo and Division Rules:**
   * **Last Digit Inspection:** We check if the last digit is zero using $n \pmod{10} = 0$.
   * **Removing Trailing Zero:** Dividing $n$ by $10$ (`n /= 10`) drops the last digit when it equals zero.
   * **Standard Decrement:** If $n \pmod{10} \ne 0$, simply decrement $n$ by $1$ (`n--`).

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Wrong Subtraction (Codeforces 977A)
 * Language: Java 17
 */
public class WrongSubtraction {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        int n = sc.nextInt();
        int k = sc.nextInt();
        sc.close();

        // Perform Tanya's subtraction rules k times
        for (int i = 0; i < k; i++) {
            if (n % 10 == 0) {
                n /= 10;
            } else {
                n--;
            }
        }

        System.out.println(n);
    }
}
```
### ⚙️ Complexity Analysis

| Complexity | Value | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(k)$ | The loop runs exactly $k$ times, performing constant-time $\mathcal{O}(1)$ operations (modulo, division, decrement) in each iteration. Since $k \le 50$, this executes almost instantaneously (~0 ms). |
| **Space Complexity** | $\mathcal{O}(1)$ | Uses a fixed number of primitive integer variables (`n`, `k`), requiring constant extra space regardless of input size. |
