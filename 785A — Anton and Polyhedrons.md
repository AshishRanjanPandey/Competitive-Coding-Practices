# ⚡ Codeforces 785A — Anton and Polyhedrons

### 📝 Problem Description
Anton's favourite geometric figures are regular polyhedrons. Note that there are five kinds of regular polyhedrons:
- **Tetrahedron**: $4$ triangular faces.
- **Cube**: $6$ square faces.
- **Octahedron**: $8$ triangular faces.
- **Dodecahedron**: $12$ pentagonal faces.
- **Icosahedron**: $20$ triangular faces.

Anton has a collection of $n$ polyhedrons. One day he decided to know how many faces his polyhedrons have in total. Help Anton and find this number!

**Input:**
- The first line contains a single integer $n$ ($1 \le n \le 200\,000$) — the number of polyhedrons in Anton's collection.
- Each of the following $n$ lines contains a string $s_i$ — the name of the $i$-th polyhedron in Anton's collection. The string can be `"Tetrahedron"`, `"Cube"`, `"Octahedron"`, `"Dodecahedron"`, or `"Icosahedron"`.

**Output:**
- Print a single integer — the total number of faces in all the polyhedrons in Anton's collection.

---

### 💡 Key Insights
1. **Mapping Polyhedrons to Face Counts:**
   - Each regular polyhedron corresponds to a fixed, known face count:
     - `Tetrahedron` $\rightarrow 4$
     - `Cube` $\rightarrow 6$
     - `Octahedron` $\rightarrow 8$
     - `Dodecahedron` $\rightarrow 12$
     - `Icosahedron` $\rightarrow 20$

2. **First-Character Optimization:**
   - Every polyhedron starts with a distinct initial character: `'T'`, `'C'`, `'O'`, `'D'`, and `'I'`.
   - Instead of comparing the full strings using string matching or hashing, we can inspect only the first character (`s.charAt(0)`) using a fast `switch` statement or an array lookup.

3. **I/O Considerations:**
   - Since $n$ can be up to $200\,000$, using fast I/O (`BufferedReader`) is significantly faster than `Scanner` and prevents potential I/O bottlenecks.

4. **Complexity:**
   - **Time Complexity:** $\mathcal{O}(n)$ — each polyhedron name is processed in $\mathcal{O}(1)$ time with a simple character check.
   - **Space Complexity:** $\mathcal{O}(1)$ — constant auxiliary memory used, processing input on the fly without storing all strings.

---

### 💻 Java Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

/**
 * Problem: Anton and Polyhedrons (Codeforces 785A)
 * Language: Java 8 / 11 / 17 / 21
 */
public class AntonAndPolyhedrons {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));

        String firstLine = reader.readLine();
        if (firstLine == null || firstLine.trim().isEmpty()) {
            return;
        }

        int n = Integer.parseInt(firstLine.trim());
        int totalFaces = 0;

        for (int i = 0; i < n; i++) {
            char initial = reader.readLine().trim().charAt(0);

            switch (initial) {
                case 'T': // Tetrahedron
                    totalFaces += 4;
                    break;
                case 'C': // Cube
                    totalFaces += 6;
                    break;
                case 'O': // Octahedron
                    totalFaces += 8;
                    break;
                case 'D': // Dodecahedron
                    totalFaces += 12;
                    break;
                case 'I': // Icosahedron
                    totalFaces += 20;
                    break;
            }
        }

        System.out.println(totalFaces);
    }
}
```
### ⏱️ Complexity Analysis

| Metric | Complexity | Explanation |
| :--- | :---: | :--- |
| **Time Complexity** | $\mathcal{O}(n)$ | Inspecting the first character takes $\mathcal{O}(1)$ time per query across $n$ polyhedrons. |
| **Auxiliary Space** | $\mathcal{O}(1)$ | Only a few primitive variables are maintained; input is processed line by line on the fly. |
