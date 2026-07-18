# 🚀 Codeforces 282A — Bit++

### 📝 Problem Description
The classic programming language of Bitland is **Bit++**. This language is peculiar as it has exactly one variable, called `X`, initialized to `0`. 

There are two operations:
* `++` increases the value of variable `X` by 1.
* `--` decreases the value of variable `X` by 1.

Given a sequence of $n$ statements, execute the program and find its final value.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Bit++ (Codeforces 282A)
 * Language: Java 17
 */
public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Read the number of statements
        int n = scanner.nextInt();
        int x = 0;
        
        // Process each statement efficiently by checking the middle character
        for (int i = 0; i < n; i++) {
            String statement = scanner.next();
            
            if (statement.charAt(1) == '+') {
                x++;
            } else {
                x--;
            }
        }
        
        // Print the final value of x
        System.out.println(x);
```

### 📊 Complexity Analysis

| Metric | Complexity | Description |
| :--- | :---: | :--- |
| **Time Complexity** | $O(n)$ | We iterate through the sequence of $n$ statements exactly once. Inside the loop, `charAt(1)` checks the character in $O(1)$ constant time. |
| **Space Complexity** | $O(1)$ | Constant auxiliary space is used. The program only stores the integer variable `x` and reads each statement one at a time without allocating memory proportional to $n$. |
        scanner.close();
    }
}
