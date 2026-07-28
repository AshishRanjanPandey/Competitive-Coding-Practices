# 🚀 Codeforces 617A — Elephant

### 📝 Problem Description
An elephant decided to visit his friend. It turned out that the elephant's house is located at point $0$ and his friend's house is located at point $x$ ($x > 0$) of the coordinate line. In one step the elephant can move $1, 2, 3, 4,$ or $5$ positions forward. Determine the minimum number of steps he needs to make in order to get to his friend's house.

**Input:**
The first line of the input contains an integer $x$ ($1 \le x \le 1\,000\,000$) — The coordinate of the friend's house.

**Output:**
Print the minimum number of steps that the elephant needs to make to get from point $0$ to point $x$.

---

### 💡 Key Insights
1. **Greedy Strategy:** To minimize the total number of steps, the elephant should always take the maximum possible step size of $5$ units as many times as possible.
2. **Ceiling Division:** If the total distance $x$ is perfectly divisible by $5$, the answer is simply $\frac{x}{5}$. If there is a remainder (1, 2, 3, or 4), that leftover distance can always be covered in **one final step**.
3. **Integer Arithmetic Trick:** Instead of using floating-point operations like `Math.ceil((double) x / 5)`, we can compute the ceiling directly using integer arithmetic: 
   $$\text{steps} = \frac{x + 4}{5}$$
4. **Efficiency:** The problem requires simple constant-time calculations. The algorithm runs in $\mathcal{O}(1)$ time complexity and uses $\mathcal{O}(1)$ space, easily passing well within the 1-second time limit and 256 MB memory limit.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Elephant (Codeforces 617A)
 * Language: Java 17
 */
public class Elephant {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        int x = sc.nextInt(); // Destination coordinate
        sc.close();
        
        // Calculate minimum steps using integer ceiling formula
        int minSteps = (x + 4) / 5;
        
        // Output the result
        System.out.println(minSteps);
    }
}
```
### ⏱️ Complexity Analysis

| Metric | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(1)$ | The solution performs a single constant-time arithmetic operation $(x + 4) / 5$, regardless of the input size $x$. |
| **Space Complexity** | $\mathcal{O}(1)$ | Only a few primitive integer variables (`x`, `minSteps`) are allocated in memory. |
