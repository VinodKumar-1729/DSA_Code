
## 📘 Print the Matrix in Spiral Manner – C++ Notes

---

### 🧩 Problem Statement

> Given a 2D matrix of size `n x m`, print the elements in **spiral order**, i.e., starting from the **top-left** corner, print the outermost elements first, then move towards the inner layers in a clockwise direction.

**Example:**

Input:

```
matrix = [
 [1,  2,  3],
 [4,  5,  6],
 [7,  8,  9]
]
```

Output:

```
[1, 2, 3, 6, 9, 8, 7, 4, 5]
```

---

### 💡 Concept

To print a matrix in **spiral order**, we simulate the movement:

1. ➡ Left to Right (Top Row)
2. ⬇ Top to Bottom (Rightmost Column)
3. ⬅ Right to Left (Bottom Row)
4. ⬆ Bottom to Top (Leftmost Column)

We continue this traversal **layer by layer** while adjusting the **boundaries**:

* `top`, `bottom`, `left`, `right` after each step.

---

### 🧪 Dry Run

#### Input:

```
matrix = [
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]
```

#### Step-by-step Traversal:

* `top = 0`, `bottom = 2`, `left = 0`, `right = 2`

1. ➡ Left to Right → `[1, 2, 3]` → `top++`
2. ⬇ Top to Bottom → `[6, 9]` → `right--`
3. ⬅ Right to Left → `[8, 7]` → `bottom--`
4. ⬆ Bottom to Top → `[4]` → `left++`
5. ➡ Left to Right → `[5]` → done

✅ Final Output: `[1, 2, 3, 6, 9, 8, 7, 4, 5]`

---

### 🧾 Pseudocode

```
function spiralOrder(matrix):
    initialize ans = empty list
    n = number of rows
    m = number of columns

    top = 0, bottom = n - 1
    left = 0, right = m - 1

    while top <= bottom and left <= right:
        for i = left to right:
            add matrix[top][i] to ans
        top++

        for i = top to bottom:
            add matrix[i][right] to ans
        right--

        if top <= bottom:
            for i = right to left:
                add matrix[bottom][i] to ans
            bottom--

        if left <= right:
            for i = bottom to top:
                add matrix[i][left] to ans
            left++

    return ans
```

---

### 💻 C++ Code (With Comments & Edge Cases)

```cpp
class Solution {
public:
    // Function to print matrix in spiral manner.
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> ans;

        // Edge Case: empty matrix
        if (matrix.empty() || matrix[0].empty()) {
            return ans;
        }

        int n = matrix.size();       // Number of rows
        int m = matrix[0].size();    // Number of columns

        int top = 0, bottom = n - 1;
        int left = 0, right = m - 1;

        // Traverse layer by layer
        while (top <= bottom && left <= right) {

            // ➡ Left to Right
            for (int i = left; i <= right; ++i) {
                ans.push_back(matrix[top][i]);
            }
            top++;

            // ⬇ Top to Bottom
            for (int i = top; i <= bottom; ++i) {
                ans.push_back(matrix[i][right]);
            }
            right--;

            // ⬅ Right to Left
            if (top <= bottom) {
                for (int i = right; i >= left; --i) {
                    ans.push_back(matrix[bottom][i]);
                }
                bottom--;
            }

            // ⬆ Bottom to Top
            if (left <= right) {
                for (int i = bottom; i >= top; --i) {
                    ans.push_back(matrix[i][left]);
                }
                left++;
            }
        }

        return ans;
    }
};
```

---

### ⚠️ Edge Cases to Consider

1. **Empty matrix**: `[]`
   ✅ Return `[]`
2. **Single row or column**:

   * `[[1, 2, 3]]` → `[1, 2, 3]`
   * `[[1], [2], [3]]` → `[1, 2, 3]`
3. **Non-square matrix**:

   * Rectangle matrix like `2x3` or `3x4` — works fine

---

### 📚 Q\&A – Interview & Exam Focus

---

#### ❓ Q1: What is the time complexity of this algorithm?

✅ **O(n × m)** — We visit each element **exactly once**

---

#### ❓ Q2: What is the space complexity?

✅ **O(n × m)** — For the output vector
(In-place printing: space is **O(1)**)

---

#### ❓ Q3: Can this be done in-place?

Yes, if you're **printing directly** instead of storing in a result array.

---

#### ❓ Q4: How would this behave with a jagged matrix (uneven rows)?

⚠️ Invalid input for this approach. A standard 2D matrix must have equal-length rows.

---

#### ❓ Q5: Is this algorithm BFS or DFS?

✅ Neither. It is a **simulation/traversal pattern** problem.

---

### 🧠 Practice MCQs

---

**Q1. What traversal directions are used in spiral printing?**

* a) Top-Down-Left-Right
* b) Zig-Zag
* ✅ c) Left→Right, Top→Bottom, Right→Left, Bottom→Top
* d) Depth First Search

---

**Q2. What condition ends the spiral traversal loop?**

* a) top == bottom and left == right
* ✅ b) top > bottom or left > right
* c) All rows are visited
* d) Matrix is square

---

**Q3. What is the output of the spiral traversal of:**

```
matrix = [
 [1, 2],
 [3, 4]
]
```

* a) \[1, 2, 3, 4]
* ✅ b) \[1, 2, 4, 3]
* c) \[1, 3, 4, 2]
* d) \[4, 3, 2, 1]

---

### ✅ Summary Table

| Feature                  | Value              |
| ------------------------ | ------------------ |
| Time Complexity          | O(n × m)           |
| Space Complexity         | O(n × m)           |
| Handles All Matrix Sizes | ✅ Yes              |
| In-place Possible        | ✅ If printing only |
| Edge Case Handling       | ✅ Included         |

---

