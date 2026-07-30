# 🚀 Codeforces 546A — Soldier and Bananas

### 📝 Problem Description
A soldier wants to buy $w$ bananas in the shop. He has to pay $k$ dollars for the first banana, $2k$ dollars for the second one, and so on (in other words, he has to pay $i \cdot k$ dollars for the $i$-th banana).

He has $n$ dollars. How many dollars does he have to borrow from his friend soldier to buy $w$ bananas?

**Input:**
The first line contains three positive integers $k, n, w$ ($1 \le k, w \le 1000$, $0 \le n \le 10^9$) — the cost of the first banana, initial number of dollars the soldier has, and number of bananas he wants.

**Output:**
Print a single integer — the amount of dollars that the soldier must borrow from his friend. If he doesn't have to borrow money, output `0`.

---

### 💡 Key Insights
1. **Arithmetic Progression:** The cost sequence for buying $w$ bananas is $k, 2k, 3k, \dots, w \cdot k$. This forms an arithmetic series that can be factored as:
   $$\text{Total Cost} = k \cdot (1 + 2 + 3 + \dots + w)$$
2. **Mathematical Sum Formula:** Instead of looping $w$ times, use the summation formula $\sum_{i=1}^{w} i = \frac{w(w + 1)}{2}$. Thus:
   $$\text{Total Cost} = k \cdot \frac{w(w + 1)}{2}$$
3. **Non-Negative Debt:** The required borrowing amount is $\text{Total Cost} - n$. If the soldier already has enough money ($\text{Total Cost} \le n$), the borrowing amount is `0`. We can handle this with $\max(0, \text{Total Cost} - n)$.
4. **Data Type Selection:** While total cost fits within standard integers, using 64-bit integers (`long` in Java) prevents potential intermediate overflow during calculation.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Soldier and Bananas (Codeforces 546A)
 * Language: Java 17
 */
public class SoldierAndBananas {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        long k = sc.nextLong(); // Cost of first banana
        long n = sc.nextLong(); // Dollars soldier currently has
        long w = sc.nextLong(); // Number of bananas wanted
        sc.close();
        
        // Calculate total cost using the sum formula: k * (w * (w + 1) / 2)
        long totalCost = k * (w * (w + 1)) / 2;
        
        // Calculate dollars to borrow
        long borrow = totalCost - n;
        
        // If borrow <= 0, he doesn't need to borrow any money
        System.out.println(Math.max(0, borrow));
    }
}
```
### ⏱️ Complexity Analysis

| Type | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(1)$ | Calculation is performed using a direct mathematical formula with basic arithmetic operations, independent of $w$. |
| **Space Complexity** | $\mathcal{O}(1)$ | Uses a fixed number of scalar variables (`k`, `n`, `w`, `totalCost`, `borrow`), requiring constant memory. |
