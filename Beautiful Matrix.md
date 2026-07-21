# 🚀 Codeforces 263A — Beautiful Matrix

### 📝 Problem Description
You've got a $5 \times 5$ matrix, consisting of 24 zeroes and a single number one. Let's index the matrix rows by numbers from 1 to 5 from top to bottom, and matrix columns by numbers from 1 to 5 from left to right. 

In one move, you are allowed to apply one of the two following transformations:
1. Swap two neighboring matrix rows (i.e., rows $i$ and $i+1$ where $1 \le i < 5$).
2. Swap two neighboring matrix columns (i.e., columns $j$ and $j+1$ where $1 \le j < 5$).

A matrix looks beautiful if the single number one is located in its middle (cell at the intersection of the 3rd row and 3rd column). 

Find the minimum number of moves needed to make the matrix beautiful.

---

### 💡 Logic Explanation
Since each swap moves the single `1` by one cell vertically or horizontally, the minimum number of swaps needed to move the `1` from position $(r, c)$ to $(3, 3)$ is given by the **Manhattan Distance**:

$$\text{Moves} = \vert{}r - 3\vert{} + \vert{}c - 3\vert{}$$

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Beautiful Matrix (Codeforces 263A)
 * Language: Java 17
 */
public class BeautifulMatrix {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        int rowOfOne = 0;
        int colOfOne = 0;
        
        // Read the 5x5 matrix to locate the '1'
        for (int i = 1; i <= 5; i++) {
            for (int j = 1; j <= 5; j++) {
                int val = sc.nextInt();
                if (val == 1) {
                    rowOfOne = i;
                    colOfOne = j;
                }
            }
        }
        
        // Calculate Manhattan distance to the center cell (3, 3)
        int moves = Math.abs(rowOfOne - 3) + Math.abs(colOfOne - 3);
        
        System.out.println(moves);
        
        sc.close();
    }
}
```
---

### ⏱️ Complexity Analysis

| Type | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(1)$ | The matrix size is fixed at $5 \times 5 = 25$ elements, so reading the input takes constant time. |
| **Space Complexity** | $\mathcal{O}(1)$ | Only a few integer variables are used to track indices; no auxiliary grid or dynamic memory is allocated. |
