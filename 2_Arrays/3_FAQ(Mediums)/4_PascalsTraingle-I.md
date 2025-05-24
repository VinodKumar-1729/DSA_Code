

## 📘 Pascal Triangle I – Complete Notes

---

### 🔶 What is Pascal’s Triangle?

Pascal's Triangle is a triangular array where the entries in the `n-th` row and `r-th` column represent the **binomial coefficient** `C(n, r)` or `nCr`, which is the number of combinations of `n` items taken `r` at a time.

It starts like this:

```
Row 0:             1
Row 1:           1   1
Row 2:         1   2   1
Row 3:       1  3   3   1
Row 4:     1  4   6   4   1
... and so on.
```

Each number is the sum of the two numbers directly above it.

---

### 🧠 Problem: Pascal Triangle I

> Given a position `r` (row) and `c` (column), return the element at that position in Pascal’s Triangle.
> **Note**: Indexing is 1-based, i.e., row and column start from 1.

---

### 🔢 Mathematical Formula Used

We use the **Binomial Coefficient formula**:

$$
C(n, r) = \frac{n!}{r!(n-r)!}
$$

But factorials can be large, so we use an optimized approach:

```cpp
for(int i = 0; i < r; i++) {
    res = res * (n - i);
    res = res / (i + 1);
}
```

This calculates `C(n, r)` in O(r) time without using large factorials.

---

### ✅ C++ Code Explained

```cpp
class Solution {
public:
    // Function to return value at position (r, c)
    int pascalTriangleI(int r, int c) {
        return nCr(r-1, c-1); // 1-based to 0-based
    }

    // Function to compute nCr (combinatorics)
    int nCr(int n, int r) {
        if(r > n - r) {
            r = n - r;  // Optimization: Use symmetry
        }
        if(r == 1) {
            return n;
        }

        int res = 1;

        for(int i = 0; i < r; i++) {
            res = res * (n - i);
            res = res / (i + 1);
        }
        return res;
    }
};
```

---

### ⏱️ Time and Space Complexity

* **Time Complexity**: O(r) — because we only loop through `r` terms.
* **Space Complexity**: O(1) — uses constant space.

---

### 🧪 Example

```cpp
Input: r = 4, c = 3
Output: 3

Explanation:
Pascal's Triangle 4th row (1-indexed): 1 3 3 1
3rd element (1-indexed) is 3.
```

---

## 📘 Applications of Pascal Triangle

* Binomial expansion (e.g., $(a + b)^n$)
* Probability and combinations
* Fibonacci sequence (diagonal sum)
* Combinatorial problems

---

## 🧩 Exam & Interview Questions with Answers

---

### 🔹 Q1: What is the value at the 5th row and 2nd column of Pascal’s Triangle?

**Answer**:
Convert to 0-based: (5-1, 2-1) → (4,1)
Using nCr: `C(4,1) = 4`
✅ **Answer: 4**

---

### 🔹 Q2: What is the time complexity of computing nCr using this method?

**Answer**:
We only loop `r` times →
✅ **Time Complexity = O(r)**
✅ **Space Complexity = O(1)**

---

### 🔹 Q3: Why do we use `r = n - r`?

**Answer**:
Due to **symmetry property** of combinations:

$$
C(n, r) = C(n, n - r)
$$

It minimizes the loop iterations, optimizing performance.

---

### 🔹 Q4: What would happen if we used factorial-based computation for nCr?

**Answer**:
It would cause **integer overflow** for large `n`, and also increase **time complexity to O(n)**.
Optimized multiplication avoids these problems.

---

### 🔹 Q5: Can Pascal’s Triangle be generated fully up to n rows?

**Answer**:
Yes, with nested loops:

```cpp
vector<vector<int>> generate(int numRows) {
    vector<vector<int>> triangle(numRows);

    for (int i = 0; i < numRows; i++) {
        triangle[i].resize(i+1);
        triangle[i][0] = triangle[i][i] = 1;

        for (int j = 1; j < i; j++) {
            triangle[i][j] = triangle[i-1][j-1] + triangle[i-1][j];
        }
    }
    return triangle;
}
```

---

### 🔹 Q6: Can Pascal Triangle be used to calculate Fibonacci Numbers?

**Answer**:
Yes, **diagonal sums** of Pascal’s Triangle yield Fibonacci numbers:

```
1
1 1
1 2 1
1 3 3 1
1 4 6 4 1

Sum diagonally like this:
1 → 1  
1 → 1  
1+1 → 2  
1+2 → 3  
1+3+1 → 5  
... → Fibonacci sequence
```

---

### 🔹 Q7: Write a function to get the entire row `r` of Pascal's Triangle.

**Answer**:

```cpp
vector<int> getRow(int r) {
    vector<int> row;
    long long val = 1;
    row.push_back(1);

    for(int i = 1; i < r; i++) {
        val = val * (r - i);
        val = val / i;
        row.push_back(val);
    }
    return row;
}
```

---

