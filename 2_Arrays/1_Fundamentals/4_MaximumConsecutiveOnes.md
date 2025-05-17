
## 📘 Maximum Consecutive Ones – C++ Notes

---

### 🧩 Problem Statement

> Given a binary array `nums`, find the **maximum number of consecutive 1s** in the array.

---

### 📌 Example

```cpp
Input: nums = {1, 1, 0, 1, 1, 1}
Output: 3

Explanation: The first two 1s are followed by a 0, then there are three consecutive 1s.
```

---

### 💡 Concept

This is a **classic sliding window problem** in disguise.

#### Core idea:

* **Count the current streak** of 1s using a `count` variable.
* **Track the maximum streak** using a `maxCount` variable.
* Reset `count` to `0` whenever a `0` is encountered.

This approach ensures you only scan the array **once** → **O(n)** time.

---

### 🔁 Dry Run

**Input:** `nums = {1, 1, 0, 1, 1, 1}`

| i | nums\[i] | count | maxCount |
| - | -------- | ----- | -------- |
| 0 | 1        | 1     | 1        |
| 1 | 1        | 2     | 2        |
| 2 | 0        | 0     | 2        |
| 3 | 1        | 1     | 2        |
| 4 | 1        | 2     | 2        |
| 5 | 1        | 3     | 3 ✅      |

📌 Final Answer: `3`

---

### 💻 Code (✅ Your Code — Correct & Efficient)

```cpp
class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& nums) {
        int count = 0;
        int maxCount = 0;
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] == 0) {
                count = 0;
            }
            if (nums[i] == 1) {
                count++;
                if (count > maxCount) {
                    maxCount = count;
                }
            }
        }
        return maxCount;
    }
};
```

✅ This code works for any binary array (only 0s and 1s).

---

### ⏱️ Time and Space Complexity

| Metric            | Value       |
| ----------------- | ----------- |
| Time Complexity   | O(n)        |
| Space Complexity  | O(1)        |
| Traversals Needed | Single pass |

---

### 🧠 Questions & Answers (Exam + Interview Focus)

---

#### ❓ Q1: What happens if the array has no 1s?

Output will be `0`.

---

#### ❓ Q2: Is there a better approach?

No. The current approach is optimal → **O(n)** time with **O(1)** space.

---

#### ❓ Q3: Can we solve this using STL?

Yes, using two pointers or iterators:

```cpp
int maxCount = 0, count = 0;
for (int num : nums) {
    count = (num == 1) ? count + 1 : 0;
    maxCount = max(maxCount, count);
}
```

---

#### ❓ Q4: What if we’re allowed to flip at most one 0?

This is a follow-up variation:

* Maintain a sliding window with at most one `0`.
* More complex but also doable in **O(n)**.

---

#### ❓ Q5: What if the array contains other numbers (not just 0 and 1)?

This code is only valid for **binary arrays**.
If there are other numbers, additional validation is needed.

---

### 📚 MCQs for Practice

---

**Q1. What is the time complexity of the current approach?**

* a) O(n²)
* b) O(log n)
* ✅ c) O(n)
* d) O(n log n)

---

**Q2. What is the output for `{0, 0, 0}`?**

✅ Output: 0

---

**Q3. For input `{1, 1, 1, 1}`, what is the output?**

✅ Output: 4

---

### ✅ Summary Table

| Feature                  | Value              |
| ------------------------ | ------------------ |
| Type                     | Array Traversal    |
| Use Case                 | Binary Arrays      |
| Time Complexity          | O(n)               |
| Space Complexity         | O(1)               |
| Handles All Cases?       | ✅ Yes              |
| Input Type               | vector<int> (0/1)  |
| Suitable for Interviews? | ✅ Frequently asked |

---

### ✨ Extra Variants (Advanced Practice)

1. **Flip at most one 0** → Max consecutive 1s after one flip
2. **K flips allowed** → Sliding window with at most K zeroes
3. **Return starting and ending indices** of max consecutive 1s
4. **Find the length of longest subarray with equal number of 0s and 1s** (Harder version)

---
