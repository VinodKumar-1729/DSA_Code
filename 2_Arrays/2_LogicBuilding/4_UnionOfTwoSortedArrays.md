
## 📝 Union of Two Sorted Arrays (C++)

---

### 📌 **Problem Statement**

> Given two **sorted arrays** `nums1[]` and `nums2[]`, return their **union** as a new **sorted array** that contains **only distinct elements**.

#### ✅ Example:

```cpp
Input:
nums1 = {1, 2, 2, 3, 4}
nums2 = {2, 4, 5, 6}

Output:
{1, 2, 3, 4, 5, 6}
```

---

### 💡 **Concept**

* The arrays are **sorted**, so we can use the **two-pointer technique**.
* Traverse both arrays simultaneously:

  * At each step, compare current elements.
  * Add the **smaller** element to the result if it's **not a duplicate**.
  * If elements are equal, add only once and move both pointers.
* After finishing one array, add the remaining elements of the other array, skipping duplicates.

#### 🎯 Key Points:

* Avoid duplicates using `unionArray.back() != nums[i/j]`
* Time-efficient: only a **single pass** through both arrays.

---

### 🔁 **Dry Run**

**Input:**

```cpp
nums1 = {1, 2, 2, 3, 4}
nums2 = {2, 4, 5, 6}
```

| i (nums1) | j (nums2) | Action                    | unionArray         |
| --------- | --------- | ------------------------- | ------------------ |
| 0 (1)     | 0 (2)     | Add 1 from nums1          | {1}                |
| 1 (2)     | 0 (2)     | Add 2 once (equal values) | {1, 2}             |
| 2 (2)     | 1 (4)     | Skip duplicate 2 in nums1 | -                  |
| 3 (3)     | 1 (4)     | Add 3 from nums1          | {1, 2, 3}          |
| 4 (4)     | 1 (4)     | Add 4 once                | {1, 2, 3, 4}       |
| 5 (end)   | 2 (5)     | Add 5 from nums2          | {1, 2, 3, 4, 5}    |
| -         | 3 (6)     | Add 6 from nums2          | {1, 2, 3, 4, 5, 6} |

---

### 💻 **C++ Code (Correct & Optimized)**

```cpp
class Solution {
public:
    vector<int> unionArray(vector<int>& nums1, vector<int>& nums2) {
        int n1 = nums1.size();
        int n2 = nums2.size();
        int i = 0, j = 0;
        vector<int> unionArray;

        while (i < n1 && j < n2) {
            if (nums1[i] <= nums2[j]) {
                if (unionArray.empty() || unionArray.back() != nums1[i]) {
                    unionArray.push_back(nums1[i]);
                }
                i++;
            } else {
                if (unionArray.empty() || unionArray.back() != nums2[j]) {
                    unionArray.push_back(nums2[j]);
                }
                j++;
            }
        }

        // Remaining elements from nums1
        while (i < n1) {
            if (unionArray.empty() || unionArray.back() != nums1[i]) {
                unionArray.push_back(nums1[i]);
            }
            i++;
        }

        // Remaining elements from nums2
        while (j < n2) {
            if (unionArray.empty() || unionArray.back() != nums2[j]) {
                unionArray.push_back(nums2[j]);
            }
            j++;
        }

        return unionArray;
    }
};
```

---

### ⏱️ **Time and Space Complexity**

| Metric          | Value                               |
| --------------- | ----------------------------------- |
| Time            | O(n + m)                            |
| Auxiliary Space | O(1) (excluding output)             |
| Result Space    | O(n + m) (in worst case all unique) |

---

### 💬 **Frequently Asked Questions (Interviews/Exams)**

---

#### ✅ Q1: **What if arrays are not sorted?**

You must **sort them first**:

* `O(n log n + m log m)` for sorting
* Then use this same two-pointer logic.

---

#### ✅ Q2: **What is the difference between union and merge?**

| Feature    | Union                               | Merge                 |
| ---------- | ----------------------------------- | --------------------- |
| Duplicates | Removed                             | Kept                  |
| Output     | Only unique values from both arrays | All elements combined |

---

#### ✅ Q3: **How does this compare to using `set` in C++?**

* Using `set<int>` is easier but **slower**:

```cpp
set<int> s;
for(int val : nums1) s.insert(val);
for(int val : nums2) s.insert(val);
```

* Complexity: O((n + m) \* log(n + m))

---

#### ✅ Q4: **What if memory usage is a concern?**

If in-place union is required:

* Not possible without modifying input or allowing duplicates.
* Space-efficient approaches will require compromise on clarity or performance.

---

### 📘 **MCQs and Exam Questions**

---

1. **What is the time complexity of union of two sorted arrays (two-pointer approach)?**
   a) O(n²)
   b) O(n log n)
   c) ✅ O(n + m)
   d) O(nm)

---

2. **Which C++ STL container automatically avoids duplicates?**
   a) vector
   b) list
   c) ✅ set
   d) stack

---

3. **Which condition avoids duplicates in your logic?**
   ✅ `unionArray.back() != nums1[i]`
   This ensures only unique values are inserted.

---

4. **If nums1 = {1, 1, 2}, nums2 = {2, 3}, what is the output?**
   ✅ Output = `{1, 2, 3}`

---

### ✅ Summary

* Efficient two-pointer method avoids duplicates **without extra space**.
* Time complexity: O(n + m)
* Great for **interviews**, **coding rounds**, and **DSA foundations**.
* Your provided code is **correct and optimal**.

---
