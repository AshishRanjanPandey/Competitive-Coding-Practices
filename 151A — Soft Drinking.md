# 🚀 Codeforces 151A — Soft Drinking

### 📝 Problem Description
This winter is so cold in Nvodsk! A group of $n$ friends decided to buy $k$ bottles of a soft drink called "Take-It-Light" to warm up a bit. Each bottle has $l$ milliliters of the drink. Also they bought $c$ limes and cut each of them into $d$ slices. After that they found $p$ grams of salt.

To make a toast, each friend needs $nl$ milliliters of the drink, a slice of lime and $np$ grams of salt. The friends want to make as many toasts as they can, provided they all drink the same amount. How many toasts can each friend make?

**Input:**
- The first and only line contains positive integers $n, k, l, c, d, p, nl, np$, not exceeding $1000$ and no less than $1$. The numbers are separated by exactly one space.

**Output:**
- Print a single integer — the number of toasts each friend can make.

---

### 💡 Key Insights
1. **Total Resource Calculation:** First, calculate the total amounts available for each ingredient:
   - Total drink = $k \times l$ milliliters
   - Total lime slices = $c \times d$ slices
   - Total salt = $p$ grams
2. **Resource-to-Toast Conversion:** Determine how many total toasts the group can make based on each individual resource by dividing the total available resource by the amount needed per toast.
3. **Bottleneck Identification:** Since a toast requires all ingredients, the maximum possible number of total toasts is limited by the scarcest resource (i.e., the minimum among the three calculated limits).
4. **Per Friend Distribution:** Finally, divide the total possible toasts equally among the $n$ friends using integer division.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

/**
 * Problem: Soft Drinking (Codeforces 151A)
 * Language: Java 17
 */
public class SoftDrinking {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        String line = reader.readLine();
        
        if (line == null || line.trim().isEmpty()) {
            return;
        }

        StringTokenizer st = new StringTokenizer(line);
        int n = Integer.parseInt(st.nextToken());
        int k = Integer.parseInt(st.nextToken());
        int l = Integer.parseInt(st.nextToken());
        int c = Integer.parseInt(st.nextToken());
        int d = Integer.parseInt(st.nextToken());
        int p = Integer.parseInt(st.nextToken());
        int nl = Integer.parseInt(st.nextToken());
        int np = Integer.parseInt(st.nextToken());

        // Calculate total amounts available
        int totalDrink = k * l;
        int totalLimes = c * d;
        int totalSalt = p;

        // Calculate how many toasts can be made from each ingredient
        int toastsFromDrink = totalDrink / nl;
        int toastsFromLimes = totalLimes; // 1 slice per toast
        int toastsFromSalt = totalSalt / np;

        // The maximum number of total toasts the group can make is the minimum of the three
        int maxTotalToasts = Math.min(toastsFromDrink, Math.min(toastsFromLimes, toastsFromSalt));

        // Divide equally among the 'n' friends
        int toastsPerFriend = maxTotalToasts / n;

        // Output the result
        System.out.println(toastsPerFriend);
    }
}
```
### 📊 Complexity Analysis

| Type | Complexity | Details |
| :--- | :--- | :--- |
| **Time Complexity** | $\mathcal{O}(1)$ | The solution performs a fixed number of basic arithmetic and comparison operations regardless of the input values. |
| **Space Complexity** | $\mathcal{O}(1)$ | Only a few primitive scalar variables are used to store inputs and intermediate results, requiring constant memory. |
