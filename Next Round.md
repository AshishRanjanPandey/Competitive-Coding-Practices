# 🚀 Codeforces 158A — Next Round

### 📝 Problem Description
"Contestant who earns a score equal to or greater than the k-th place finisher's score will advance to the next round, as long as the contestant earns a positive score..." — an excerpt from contest rules.

A total of $n$ participants took park in the contest ($n \ge k$), and you already know their scores. Calculate how many participants will advance to the next round.

---

### 💻 Java Solution

```java
import java.util.Scanner;

/**
 * Problem: Next Round (Codeforces 158A)
 * Language: Java 17
 */
public class NextRound {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Read n (total participants) and k (the benchmark place)
        int n = sc.nextInt();
        int k = sc.nextInt();
        
        int[] scores = new int[n];
        for (int i = 0; i < n; i++) {
            scores[i] = sc.nextInt();
        }
        
        // Find the score of the k-th place finisher
        // Arrays are 0-indexed, so the k-th place is at index k - 1
        int targetScore = scores[k - 1];
        
        int advancers = 0;
        for (int i = 0; i < n; i++) {
            // A participant advances if their score is >= targetScore AND > 0
            if (scores[i] >= targetScore && scores[i] > 0) {
                advancers++;
            } else {
                // Since the array is non-increasing, if this participant 
                // doesn't qualify, none of the following will either.
                break;
            }
        }
        
        System.out.println(advancers);
        sc.close();
    }
}
```
### 📊 Complexity Analysis

| Complexity Type | Notation | Explanation |
| :--- | :--- | :--- |
| **Time Complexity** | $O(n)$ | We iterate through the array of scores exactly once to find the qualifiers. In the best-case scenario (where scores drop to `0` or below the $k$-th score early), the loop breaks even sooner. |
| **Space Complexity** | $O(n)$ | We store the $n$ scores in an integer array to easily look up the $k$-th place finisher's score before processing. |
