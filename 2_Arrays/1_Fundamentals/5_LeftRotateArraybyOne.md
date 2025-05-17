
## 📘 Left Rotate Array by One 

---

### 🧩 Problem Statement

> Given an array of integers, **rotate it to the left by one position**.
> This means that the **first element moves to the last**, and every other element shifts one position to the left.

---

### 🧠 Example

```cpp
Input:  nums = {1, 2, 3, 4, 5}
Output: nums = {2, 3, 4, 5, 1}
```

---

### 💡 Concept

**Left Rotation by One:**

* Store the **first element** in a temporary variable.
* Shift every element one index to the **left**.
* Place the saved first element at the **end**.

#### 🔁 Visual Illustration:

```text
Original:     [1, 2, 3, 4, 5]
Step 1: Save 1
Step 2: Shift → [2, 3, 4, 5, _]
Step 3: Place 1 → [2, 3, 4, 5, 1]
```

* Time Complexity: **O(n)**
* Space Complexity: **O(1)** (in-place)

---

### 🧪 Dry Run

#### Input:

```cpp
nums = {10, 20, 30, 40}
```

| Step | Operation                 | Array              |
| ---- | ------------------------- | ------------------ |
| Init | Store first → `last = 10` | {10, 20, 30, 40}   |
| i=0  | `nums[0] = nums[1]`       | {20, 20, 30, 40}   |
| i=1  | `nums[1] = nums[2]`       | {20, 30, 30, 40}   |
| i=2  | `nums[2] = nums[3]`       | {20, 30, 40, 40}   |
| End  | `nums[3] = last (10)`     | {20, 30, 40, 10} ✅ |

---

### 💻 Code (✅ Correct Code)

```cpp
class Solution {
public:
    void rotateArrayByOne(vector<int>& nums) {
        int last = nums[0];
        int n = nums.size();

        for(int i = 0; i < n - 1; i++) {
            nums[i] = nums[i + 1];
        }
        nums[n - 1] = last;
    }
};
```

---

### ⏱️ Time & Space Complexity

| Metric           | Value    |
| ---------------- | -------- |
| Time Complexity  | O(n)     |
| Space Complexity | O(1)     |
| Type             | In-place |

---

### 📚 Q\&A – Interview + Exam Focus

---

#### ❓ Q1: Can we rotate the array right instead?

Yes, but the logic changes. You would store the **last** element, shift elements to the **right**, and insert the saved value at the beginning.

---

#### ❓ Q2: What if the array has only one element?

✅ No change. The rotation will result in the same array.

```cpp
Input: [5] → Output: [5]
```

---

#### ❓ Q3: What if the array is empty?

⚠️ Your current code will throw an error (`nums[0]` access).
**Fix for robustness:**

```cpp
if (nums.empty()) return;
```

---

#### ❓ Q4: Can we rotate the array multiple times?

Yes. Rotate `k` times by calling the function `k` times (inefficient)
Or use the **Juggling Algorithm** or **Reversal Algorithm** for better performance → O(n) with fewer rotations.

---

#### ❓ Q5: Is STL available for this?

Yes. Using `std::rotate` from `<algorithm>`:

```cpp
rotate(nums.begin(), nums.begin() + 1, nums.end());
```

It rotates left by one in a single line.

---

### ✅ Summary Table

| Feature                  | Value              |
| ------------------------ | ------------------ |
| Type                     | Array Manipulation |
| Operation                | Left Shift by 1    |
| In-place                 | ✅ Yes              |
| Time Complexity          | O(n)               |
| Space Complexity         | O(1)               |
| STL Alternative          | `std::rotate`      |
| Suitable for Interviews? | ✅ Yes              |

---

### 📘 Practice MCQs

---

**Q1. What is the time complexity of left rotating an array by one element?**

* a) O(1)
* ✅ b) O(n)
* c) O(n²)
* d) O(log n)

---

**Q2. What will be the result of rotating `{5, 6, 7, 8}` left by one?**

✅ Output: `{6, 7, 8, 5}`

---

**Q3. Which STL function helps to rotate an array?**

✅ `std::rotate(begin, middle, end)`

---

