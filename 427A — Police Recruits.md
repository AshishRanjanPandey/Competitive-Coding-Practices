# 🚀 Codeforces 427A — Police Recruits

### 📝 Problem Description
The police department of your city has just started its journey. Initially, they don't have any manpower, so they started hiring new recruits in groups. 

Meanwhile, crimes keep occurring within the city. Each member of the police force can investigate only one crime during their lifetime. If there is no police officer free (not busy with a crime) during the occurrence of a crime, it will go untreated. Given the chronological order of crime occurrences and recruit hirings, find the number of crimes which will go untreated.

**Input:**
- The first line contains an integer $n$ ($1 \le n \le 10^5$) — the number of events.
- The second line contains $n$ space-separated integers. If the integer is `-1`, it means a crime has occurred. Otherwise, the integer will be positive, representing the number of officers recruited together at that time (no more than $10$ officers are recruited at a time).

**Output:**
- Print a single integer: the total number of crimes which will go untreated.

---

### 💡 Key Insights
1. **Greedy State Tracking:** We can track the state of available manpower using a running counter `officers` and another counter `untreatedCrimes` to accumulate the total uninvestigated crimes.
2. **Handling Events:** 
   - If we encounter a crime (`-1`), we check if `officers > 0`. If yes, we decrement `officers` (since one officer is now busy). If no, we increment `untreatedCrimes`.
   - If we encounter a positive integer, we add it directly to our `officers` pool.
3. **Efficiency:** A single linear scan through the input tokens allows us to process everything efficiently within time limits.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Police Recruits (Codeforces 427A)
 * Language: Java 17
 */
public class PoliceRecruits {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        String line = reader.readLine();
        if (line == null) {
            return;
        }
        
        int n = Integer.parseInt(line.trim());
        StringTokenizer st = new StringTokenizer(reader.readLine());
        
        int officers = 0;
        int untreatedCrimes = 0;
        
        for (int i = 0; i < n; i++) {
            int event = Integer.parseInt(st.nextToken());
            
            if (event == -1) {
                // If officers are available, assign one to the crime
                if (officers > 0) {
                    officers--;
                } else {
                    // No officer available, crime goes untreated
                    untreatedCrimes++;
                }
            } else {
                // New officers are recruited
                officers += event;
            }
        }
        
        System.out.println(untreatedCrimes);
    }
}
```
### 📊 Complexity Analysis

| Type | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | We iterate through the $n$ events exactly once using fast I/O (`BufferedReader` and `StringTokenizer`). |
| **Space Complexity** | $\mathcal{O}(1)$ | Only a few scalar primitive variables (`n`, `officers`, `untreatedCrimes`, `event`) are used for computation. |
