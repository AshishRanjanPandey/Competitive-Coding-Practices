# 🚀 Codeforces 4A — Watermelon

### 📝 Problem Description
One hot summer day Pete and his friend Billy decided to buy a watermelon. They chose the biggest and the ripest one, in their opinion. After that the watermelon was weighed, and the scales showed `w` kilos. They rushed home, dying of thirst, and decided to divide the berry, however they faced a hard problem.

Pete and Billy are great fans of even numbers, that's why they want to divide the watermelon in such a way that each of the two parts weighs an **even number of kilos**, at the same time it is not obligatory that the parts are equal. For sure, each of them should get a part of **positive weight**.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Watermelon (Codeforces 4A)
 * Language: Java 17
 */
public class Watermelon {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int w = sc.nextInt();
        
        // Check if the weight is even and strictly greater than 2
        if (w % 2 == 0 && w > 2) {
            System.out.println("YES");
        } else {
            System.out.println("NO");
        }
        
        sc.close();
    }
}
```
| Metric | Complexity | Description |
| :--- | :---: | :--- |
| **Time Complexity** | $\mathcal{O}(1)$ | **Constant Time.** Basic arithmetic checks execute instantly. |
| **Space Complexity** | $\mathcal{O}(1)$ | **Constant Space.** Uses a single variable. |
