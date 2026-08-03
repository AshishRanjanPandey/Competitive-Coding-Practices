# 🚀 Codeforces 69A — Young Physicist

### 📝 Problem Description
A guy named Vasya attends the final grade of a high school. One day Vasya decided to watch a match of his favorite hockey team. And, as the boy loves hockey very much, even more than physics, he forgot to do the homework. Specifically, he forgot to complete his physics tasks. Next day the teacher got very angry at Vasya and decided to teach him a lesson. He gave the lazy student a seemingly easy task: You are given an idle body in space and the forces that affect it. The body can be considered as a material point with coordinates (0; 0; 0). Vasya had only to answer whether it is in equilibrium. 

"Piece of cake" — thought Vasya, we need only to check if the sum of all vectors is equal to 0. So, Vasya began to solve the problem. But later it turned out that there can be lots and lots of these forces, and Vasya can not cope without your help. Help him. Write a program that determines whether a body is idle or is moving by the given vectors of forces.

**Input:**
The first line contains a positive integer $n$ ($1 \le n \le 100$), then follow $n$ lines containing three integers each: the $x_i$ coordinate, the $y_i$ coordinate and the $z_i$ coordinate of the force vector, applied to the body ($-100 \le x_i, y_i, z_i \le 100$).

**Output:**
Print the word `YES` if the body is in equilibrium, or the word `NO` if it is not.

---

### 💡 Key Insights
1. **Vector Equilibrium Condition:** For a body in 3D space to remain in static equilibrium, the net force vector acting on it must be zero ($\vec{F}_{net} = \vec{0}$).
2. **Component-Wise Independent Sums:** Vector addition breaks down into scalar addition along each axis independently:
   $$\sum_{i=1}^{n} x_i = 0, \quad \sum_{i=1}^{n} y_i = 0, \quad \sum_{i=1}^{n} z_i = 0$$
3. **Single Pass Accumulation:** Maintain running totals for the $x$, $y$, and $z$ coordinates while reading input. Check if all three running sums equal $0$ at the end.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Young Physicist (Codeforces 69A)
 * Language: Java 17
 */
public class YoungPhysicist {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        if (!sc.hasNextInt()) {
            return;
        }

        int n = sc.nextInt();

        int sumX = 0;
        int sumY = 0;
        int sumZ = 0;

        // Read vectors and accumulate force components for each axis
        for (int i = 0; i < n; i++) {
            sumX += sc.nextInt();
            sumY += sc.nextInt();
            sumZ += sc.nextInt();
        }
        sc.close();

        // Body is in equilibrium only if the net force along all 3 axes is zero
        if (sumX == 0 && sumY == 0 && sumZ == 0) {
            System.out.println("YES");
        } else {
            System.out.println("NO");
        }
    }
}
```
### ⚙️ Complexity Analysis

| Type | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | Processes each of the $n$ force vectors once in a single loop. |
| **Space Complexity** | $\mathcal{O}(1)$ | Uses a constant amount of extra memory for accumulator variables (`sumX`, `sumY`, `sumZ`). |
