# 🚀 Codeforces 231A — Team

### 📝 Problem Description
One day three best friends Petya, Vasya and Tonya decided to form a team and take part in programming contests. Participants are usually offered several problems during programming contests. 

Long before the start the friends decided that they will implement a problem **if at least two of them are sure about the solution**. Otherwise, the friends won't write the problem's solution.

This contest offers $n$ problems to the participants. For each problem we know, which friend is sure about the solution. Help the friends find the number of problems for which they will write a solution.

---

### 💻 Java Solution

```java
import java.util.Scanner;
 
/**
 * Problem: Team (Codeforces 231A)
 * Language: Java 17
 */
public class Team {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Read the number of problems
        int n = scanner.nextInt();
        int solvedCount = 0;
        
        // Loop through each problem
        for (int i = 0; i < n; i++) {
            int petya = scanner.nextInt();
            int vasya = scanner.nextInt();
            int tonya = scanner.nextInt();
            
            // Check if at least two friends know the solution
            if (petya + vasya + tonya >= 2) {
                solvedCount++;
            }
        }
        
        // Print the final count of implemented problems
        System.out.println(solvedCount);
        
        scanner.close();
    }
}
```
| Metric | Complexity | Description |
| :--- | :---: | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | **Linear Time.** The program loops through the $n$ problems exactly once. Inside the loop, reading the inputs and adding them takes $\mathcal{O}(1)$ constant time. |
| **Space Complexity** | $\mathcal{O}(1)$ | **Constant Space.** The algorithm only uses a few primitive integer variables (`n`, `solvedCount`, `petya`, `vasya`, `tonya`), allocating no extra memory dynamically. |
