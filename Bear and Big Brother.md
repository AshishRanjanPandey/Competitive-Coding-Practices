# 🚀 Codeforces 791A — Bear and Big Brother

### 📝 Problem Description
Bear Limak wants to become the largest of bears, or at least to become larger than his brother Bob. Right now, Limak and Bob weigh $a$ and $b$ respectively. It's guaranteed that Limak's weight is smaller than or equal to his brother's weight.

Limak eats a lot and his weight is tripled after every year, while Bob's weight is doubled after every year. After how many full years will Limak become strictly larger (strictly heavier) than Bob?

**Input:**
The only line of the input contains two integers $a$ and $b$ ($1 \le a \le b \le 10$) — the weight of Limak and the weight of Bob respectively.

**Output:**
Print one integer, denoting the integer number of years after which Limak will become strictly larger than Bob.

---

### 💡 Key Insights
1. **Simulation Approach:** Since the upper bound for the initial weights is extremely small ($a, b \le 10$), Limak's exponential growth ($3^y$) quickly surpasses Bob's growth ($2^y$). Simple year-by-year simulation using a `while` loop is both optimal and straightforward.
2. **Strict Inequality:** The termination condition requires Limak to be *strictly greater* than Bob ($a > b$). The loop must continue as long as $a \le b$.
3. **Simultaneous Growth:** In each step/year, both weight transformations must happen together: Limak's weight multiplies by 3 (`a *= 3`) and Bob's weight multiplies by 2 (`b *= 2`).
4. **Efficiency:** The algorithm takes $\mathcal{O}(\log_{3/2}(b/a))$ iterations, which is at most $6$ loops for the given constraints ($N \le 10$). Time complexity is $\mathcal{O}(1)$ and space complexity is $\mathcal{O}(1)$.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Bear and Big Brother (Codeforces 791A)
 * Language: Java 17
 */
public class BearAndBigBrother {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        int a = sc.nextInt(); // Limak's initial weight
        int b = sc.nextInt(); // Bob's initial weight
        sc.close();
        
        int years = 0;
        
        // Simulate year by year until Limak is strictly heavier than Bob
        while (a <= b) {
            a *= 3; // Limak triples his weight
            b *= 2; // Bob doubles his weight
            years++;
        }
        
        // Output the required number of full years
        System.out.println(years);
    }
}
```
### 📊 Complexity Analysis

| Complexity | Scale | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(\log_{1.5}(b/a)) \approx \mathcal{O}(1)$ | The loop runs at most 6 times for the constraint $a, b \le 10$. In general, it terminates when $a \cdot 3^k > b \cdot 2^k \implies (1.5)^k > b/a$. |
| **Space Complexity** | $\mathcal{O}(1)$ | Uses a constant amount of extra memory to store scalar integer variables (`a`, `b`, and `years`). |
