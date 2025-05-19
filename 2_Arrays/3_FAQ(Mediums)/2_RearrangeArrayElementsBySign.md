
## 📘 Rearrange Array Elements by Sign 

---

### 🧩 Problem Statement

> Given an array `nums` of **even length**, where the count of **positive** and **negative** integers is **equal**, rearrange the elements such that:

* Positive and negative numbers **alternate**.
* The **first element** is **positive**.

You must return the **rearranged array**.

---

### 💡 Concept

Given the problem constraints:

* The number of positive and negative integers is equal.
* The array length is even.
* We must alternate signs starting with a **positive number**.

**Approach**:

* Traverse the array once.
* Use two pointers:

  * `posIndex` → fill positive numbers at **even indices** (`0, 2, 4, ...`)
  * `negIndex` → fill negative numbers at **odd indices** (`1, 3, 5, ...`)

This ensures:

* Alternating pattern ✅
* Starting with positive number ✅

**Time Complexity**: `O(n)`
**Space Complexity**: `O(n)` (due to extra result array)

---

### 🧪 Dry Run

#### Input:

```cpp
nums = [3, -1, 2, -5]
```

#### Step-by-step Execution:

* `posIndex = 0`, `negIndex = 1`
* i = 0 → 3 > 0 → `arr[0] = 3`, `posIndex = 2`
* i = 1 → -1 < 0 → `arr[1] = -1`, `negIndex = 3`
* i = 2 → 2 > 0 → `arr[2] = 2`, `posIndex = 4`
* i = 3 → -5 < 0 → `arr[3] = -5`, `negIndex = 5`

✅ Output: `[3, -1, 2, -5]`

---

### 🧾 Pseudocode

```
function rearrangeArray(nums):
    n = size of nums
    arr = new array of size n
    posIndex = 0
    negIndex = 1

    for i = 0 to n-1:
        if nums[i] >= 0:
            arr[posIndex] = nums[i]
            posIndex += 2
        else:
            arr[negIndex] = nums[i]
            negIndex += 2

    return arr
```

---

### 💻 C++ Code (Optimized with Comments)

```cpp
class Solution {
public:
    vector<int> rearrangeArray(vector<int>& nums) {
        int n = nums.size();
        vector<int> arr(n, 0); // Result array to hold rearranged elements

        int posIndex = 0; // Even indices for positive numbers
        int negIndex = 1; // Odd indices for negative numbers

        for (int i = 0; i < n; i++) {
            if (nums[i] >= 0) {
                arr[posIndex] = nums[i];
                posIndex += 2;
            } else {
                arr[negIndex] = nums[i];
                negIndex += 2;
            }
        }

        return arr;
    }
};
```

#### ✅ Key Points:

* Edge Case: Assumes **equal number** of positives and negatives
* Starts with positive as required
* `>= 0` used to treat `0` as positive (adjust if needed)

---

### 📚 Q\&A – Interview & Exam Focus

---

#### ❓ Q1: What is the time complexity?

✅ **O(n)** – Single pass through array

---

#### ❓ Q2: What is the space complexity?

✅ **O(n)** – Uses an extra array of the same size

---

#### ❓ Q3: Why do we place positives at even indices?

To meet the condition:

> Alternating signs starting with a **positive number** at index `0` (even)

---

#### ❓ Q4: Can we do it **in-place**?

Only if we **don't care** about order of same-sign elements and allow extra complexity. It’s possible but **not easy or recommended** for interviews unless asked.

---

#### ❓ Q5: How would you handle if counts of positive and negative numbers are **not equal**?

Then we need a **more general approach**:

* Traverse and fill alternately until one of the types runs out
* Then fill remaining numbers at the end
  ✅ Not covered in this code (as it violates original constraint)

---

#### ❓ Q6: Is 0 considered positive?

In this code: **Yes** (because of `nums[i] >= 0`)
In real-world problems, **confirm with interviewer** or problem statement

---

### ✅ Summary Table

| Feature                   | Value          |
| ------------------------- | -------------- |
| Time Complexity           | O(n)           |
| Space Complexity          | O(n)           |
| Starts with Positive?     | ✅ Yes          |
| Handles Equal Count       | ✅ Yes          |
| Handles Unequal Count     | ❌ No           |
| Treats 0 as Positive?     | ✅ Yes (`>= 0`) |
| Stable (preserves order)? | ✅ Yes          |

---

### 🧠 Practice MCQs

---

**Q1. What does the algorithm assume about the input?**

* a) All elements are positive
* ✅ b) Equal positive and negative numbers
* c) Array is sorted
* d) Input length is odd

---

**Q2. Which index do positive numbers go to in the rearranged array?**

* a) Odd indices
* ✅ b) Even indices
* c) End of the array
* d) None of the above

---

**Q3. What would happen if the input had more positives than negatives?**

* a) Code runs fine
* b) Code crashes
* ✅ c) Index out of bounds
* d) Output will be incorrect but no crash

---
