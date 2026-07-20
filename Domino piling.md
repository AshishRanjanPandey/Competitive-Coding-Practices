# 🚀 Codeforces 50A — Domino Piling

### 📝 Problem Description
You are given a rectangular board of $M \times N$ squares. Also you are given an unlimited number of standard domino pieces of $2 \times 1$ squares. You are allowed to rotate the pieces. You are asked to place as many dominoes as possible on the board so as to meet the following conditions:

1. Each domino completely covers two squares.
2. No two dominoes overlap.
3. Each domino lies entirely inside the board. It is allowed to touch the edges of the board.

Find the maximum number of dominoes, which can be placed under these restrictions.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Domino Piling (Codeforces 50A)
 * Language: Java 17
 */
public class DominoPiling {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Read board dimensions M and N
        int m = sc.nextInt();
        int n = sc.nextInt();
        
        // Each domino covers 2 squares.
        // The maximum dominoes is the total board area integer divided by 2.
        int maxDominoes = (m * n) / 2;
        
        System.out.println(maxDominoes);
        
        sc.close();
    }
}
```
---

### ⏱️ Complexity Analysis

| Type | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(1)$ | The solution performs a single constant-time arithmetic operation `(M * N) / 2`. |
| **Space Complexity** | $\mathcal{O}(1)$ | Uses a constant amount of memory to store the integer dimensions $M$ and $N$. |
