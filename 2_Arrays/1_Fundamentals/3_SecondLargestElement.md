
## 📘 Second Largest Element in an Array (Linear Search) – C++

---

### 🧩 Problem Statement

> Given an array of integers, find the **second largest unique element**.
> If no such element exists (e.g. all elements are equal or only one element), return `-1`.

---

### 📌 Example

```cpp
Input: nums = {10, 5, 20, 20}
Output: 10

Input: nums = {7, 7, 7}
Output: -1
```

---

### 💡 Concept

* We need to **track two values**:

  * `largest`: The largest element found so far.
  * `secondLargest`: The next highest element, less than `largest`.

* Traverse the array once and update both values using conditional checks.

* Handle **edge cases**:

  * Arrays with fewer than 2 elements
  * All elements are the same

---

### 🔁 Dry Run

**Input:** `nums = {12, 35, 1, 10, 34, 1}`

| Step | i | nums\[i] | largest | secondLargest | Condition         |
| ---- | - | -------- | ------- | ------------- | ----------------- |
| 0    | 0 | 12       | 12      | INT\_MIN      | New largest       |
| 1    | 1 | 35       | 35      | 12            | New largest       |
| 2    | 2 | 1        | 35      | 12            | No change         |
| 3    | 3 | 10       | 35      | 12            | No change         |
| 4    | 4 | 34       | 35      | 34            | New secondLargest |
| 5    | 5 | 1        | 35      | 34            | No change         |

✅ Final Answer: 34

---

### 💻 Code (Your Code – Correct and Clean)

```cpp
class Solution {
public:
    int secondLargestElement(vector<int>& nums) {
        int n = nums.size();
        if (n < 2) {
            return -1;  // Not enough elements
        }

        int largest = INT_MIN;
        int secondLargest = INT_MIN;

        for (int i = 0; i < n; i++) {
            if (nums[i] > largest) {
                secondLargest = largest;
                largest = nums[i];
            } else if (nums[i] > secondLargest && nums[i] != largest) {
                secondLargest = nums[i];
            }
        }

        return (secondLargest == INT_MIN) ? -1 : secondLargest;
    }
};
```

---

### ⏱️ Time and Space Complexity

| Metric            | Value  |
| ----------------- | ------ |
| Time Complexity   | O(n)   |
| Space Complexity  | O(1)   |
| Traversals Needed | 1 pass |

---

### 🧠 Questions & Answers (Exam + Interview Focus)

---

#### ❓ Q1: Why initialize `secondLargest` with `INT_MIN`?

✅ Because elements can be negative. If we use 0, it might ignore valid negative numbers.

---

#### ❓ Q2: What if all elements are the same?

Then there’s **no second unique largest**, so return `-1`.
Example: `{5, 5, 5}` → output: `-1`.

---

#### ❓ Q3: Can this be done in two passes?

Yes:

1. First pass → find largest
2. Second pass → find max element < largest

But it's **less efficient** (O(2n) vs O(n)).

---

#### ❓ Q4: Can sorting be used?

Yes:

```cpp
sort(nums.begin(), nums.end(), greater<int>());
```

Then loop for first different value.
But sorting takes **O(n log n)** and modifies the array, which may not be desirable.

---

#### ❓ Q5: How to handle duplicates?

Already handled in the condition:

```cpp
nums[i] != largest
```

---

### 📚 MCQs for Practice

---

**Q1. What is the time complexity of finding the second largest using a single loop?**

* a) O(1)
* ✅ b) O(n)
* c) O(n log n)
* d) O(n²)

---

**Q2. What will the code return for nums = {-2, -5, -1, -7}?**

✅ Output: -2 (largest = -1, second largest = -2)

---

**Q3. In which case will the function return -1?**

* a) nums = {10}
* b) nums = {10, 10, 10}
* ✅ c) Both a and b

---

### ✅ Summary Table

| Feature             | Value                   |
| ------------------- | ----------------------- |
| Algorithm           | Linear Search           |
| Approach            | Single Pass             |
| Time Complexity     | O(n)                    |
| Space Complexity    | O(1)                    |
| Handles Duplicates? | ✅ Yes                   |
| Returns -1 If?      | <2 elements or all same |

---

### ✨ Extra Challenges

1. Modify to return **index** of the second largest.
2. Find **second smallest** element.
3. Handle **floating-point** arrays.

---
