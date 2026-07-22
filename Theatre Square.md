# 🚀 Codeforces 1A — Theatre Square

### 📝 Problem Description
Theatre Square in the capital city of Berland has a rectangular shape with the size $n \times m$ meters. On the occasion of the city's anniversary, a decision was taken to pave the Square with square granite flagstones. Each flagstone is of the size $a \times a$.

What is the least number of flagstones needed to pave the Square? It's allowed to cover the surface larger than the Theatre Square, but the Square has to be covered. It's not allowed to break the flagstones. The sides of flagstones should be parallel to the sides of the Square.

---

### 💡 Key Insights
1. **Independent Dimensions:** Since flagstones cannot be broken and their sides must lie parallel to the sides of the square, you cover the length ($n$) and width ($m$) independently using stones of size $a$.
2. **Ceiling Division:** The number of flagstones along a side of length $x$ is $\lceil x / a \rceil$. In integer arithmetic, ceiling division can be calculated without floating-point errors as `(x + a - 1) / a`.
3. **64-bit Integer Overflow:** Given $1 \le n, m, a \le 10^9$, the total flagstones required can be up to $10^{18}$. This exceeds 32-bit signed integers (`int`), so 64-bit integers (`long` in Java) are required.

---

### 💻 Java Solution

import java.util.Scanner;

public class TheatreSquare {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Read dimensions N, M and flagstone side length A
        long n = sc.nextLong();
        long m = sc.nextLong();
        long a = sc.nextLong();

        // Compute flagstones needed along length and width using ceiling division
        long lengthStones = (n + a - 1) / a;
        long widthStones = (m + a - 1) / a;

        // Total flagstones needed is the product of both sides
        long totalStones = lengthStones * widthStones;

        System.out.println(totalStones);

        sc.close();
    }
}

---

### ⏱️ Complexity
* **Time Complexity:** $\mathcal{O}(1)$ — constant time arithmetic calculations.
* **Space Complexity:** $\mathcal{O}(1)$ — uses fixed memory space for scalar variables.
