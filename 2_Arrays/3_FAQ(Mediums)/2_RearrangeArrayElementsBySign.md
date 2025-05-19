
## 📘 Rearrange Array Elements by Sign 

---

### 🧩 Problem Statement

> Given an array `nums` of **even length**, where the number of **positive** and **negative** integers is **equal**, rearrange the elements such that:

* Positive and negative numbers **alternate**.
* The **first** element is **positive**.

🧠 **Return the rearranged array**.
**Constraints**: No extra constraints on element values; only number of positives == number of negatives.

---

### 💡 Concept

We know:

* The number of positives = number of negatives.
* The output should alternate: `pos, neg, pos, neg,...`

🔁 Strategy:

* Use a new array of size `n`.
* Place **positives at even indices** (`0, 2, 4...`) and **negatives at odd indices** (`1, 3, 5...`).

This ensures:

* Alternating signs ✅
* First element positive ✅

📈 **Time Complexity**: O(n)
📦 **Space Complexity**: O(n) (due to extra array)

---

### 🧪 Dry Run

#### Input:

```java
nums = [3, -2, 1, -4]
```

#### Step-by-Step:

* posIndex = 0, negIndex = 1
* i = 0 → 3 → positive → arr\[0] = 3, posIndex += 2 → posIndex = 2
* i = 1 → -2 → negative → arr\[1] = -2, negIndex += 2 → negIndex = 3
* i = 2 → 1 → positive → arr\[2] = 1, posIndex = 4
* i = 3 → -4 → negative → arr\[3] = -4

✅ Output: `[3, -2, 1, -4]`

---

### 🧾 Pseudocode

```
function rearrangeArray(nums):
    n = length of nums
    create new array result of size n
    posIndex = 0
    negIndex = 1

    for i = 0 to n-1:
        if nums[i] > 0:
            result[posIndex] = nums[i]
            posIndex += 2
        else:
            result[negIndex] = nums[i]
            negIndex += 2

    return result
```

---

### 💻 Java Code (✅ Optimized + Edge Case Comments)

```java
class Solution { 
    public int[] rearrangeArray(int[] nums) {
        int n = nums.length;
        int[] arr = new int[n];

        // posIndex for even indices, negIndex for odd indices
        int posIndex = 0, negIndex = 1;

        for (int i = 0; i < n; i++) {
            if (nums[i] > 0) {
                arr[posIndex] = nums[i];
                posIndex += 2;
            } else {
                arr[negIndex] = nums[i];
                negIndex += 2;
            }
        }

        return arr;
    }
}
```

#### 🔍 Edge Cases Handled:

* Equal number of positive and negative → as per constraint ✅
* Array of size 2 → handled gracefully ✅
* Duplicate values → allowed and supported ✅
* All positive or all negative? ❌ Not valid per constraint

---

### 📚 Q\&A – Interview & Exam Focus

---

#### ❓ Q1: Why can't we do this in-place?

Because maintaining alternating positions **without overwriting** is complex. An auxiliary array is the simplest and cleanest approach.

---

#### ❓ Q2: What's the time and space complexity?

* **Time:** O(n) (single traversal)
* **Space:** O(n) (due to result array)

---

#### ❓ Q3: Can we solve it in O(1) space?

Yes, **in-place rearrangement** is possible using two-pointer swaps **only** when we don’t care about the original order of positives/negatives and want **alternating signs only**. But it's complex and risky to implement.

---

#### ❓ Q4: Can the input have zero?

Depends on definition:

* If `0` is treated as **neither** → ignore or raise error
* If `0` is treated as **positive** → works fine

👆 In most problems, **0 is neither positive nor negative**.

---

#### ❓ Q5: What if positives and negatives are not equal in count?

The algorithm will fail. It assumes perfect balance.

🔁 For unbalanced arrays:

* Count positives and negatives
* Fill alternately as much as possible
* Add remaining at the end (complex)

---

### 🧠 Practice MCQs

---

**Q1. What is the time complexity of this solution?**

* a) O(log n)
* ✅ b) O(n)
* c) O(n²)
* d) O(1)

---

**Q2. What condition must the input array satisfy?**

* ✅ a) Equal positive and negative count
* b) Sorted input
* c) No duplicates
* d) All positive numbers

---

**Q3. Where are positive numbers placed in the output?**

* a) Odd indices
* ✅ b) Even indices
* c) At the end
* d) Randomly

---

### ✅ Summary Table

| Feature                   | Value                                |
| ------------------------- | ------------------------------------ |
| Goal                      | Alternate signs, start with positive |
| Time Complexity           | O(n)                                 |
| Space Complexity          | O(n)                                 |
| In-place                  | ❌ (uses extra array)                 |
| Works when sign counts ≠? | ❌ No                                 |
| Handles zero              | ⚠️ Only if specified                 |

---
