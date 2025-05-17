

## 📝 Linear Search (C++)

---

### 📌 **Problem Statement**

> Given an array `nums[]` and a `target` element, find the **index of the first occurrence** of the target using **linear search**.
> If the element is not found, return `-1`.

---

### ✅ **Example**

```cpp
Input: nums = {5, 3, 7, 1, 9}, target = 1  
Output: 3  
Explanation: Element 1 is at index 3
```

---

### 💡 **Concept**

* **Linear Search** is the **simplest** searching technique.
* We iterate through the array from start to end.
* At each index `i`, we check if `nums[i] == target`.

  * If yes, return index `i`.
  * If no match is found till end, return `-1`.

#### 🎯 When to Use Linear Search:

* For **unsorted arrays**.
* For **small datasets**.
* When performance isn't a strict concern.

---

### 🔁 **Dry Run**

#### Input:

```cpp
nums = {10, 20, 30, 40, 50}, target = 30
```

| Step | i | nums\[i] | Comparison | Result         |
| ---- | - | -------- | ---------- | -------------- |
| 1    | 0 | 10       | 10 == 30 ❌ | Continue       |
| 2    | 1 | 20       | 20 == 30 ❌ | Continue       |
| 3    | 2 | 30       | 30 == 30 ✅ | Return index 2 |

---

### 💻 **C++ Code (Correct and Efficient)**

```cpp
class Solution {
public:
    int linearSearch(vector<int>& nums, int target) {
        for(int i = 0; i < nums.size(); i++) {
            if(nums[i] == target) {
                return i; // Return the index of first match
            }
        }
        return -1; // Element not found
    }
};
```

---

### ⏱️ **Time and Space Complexity**

| Metric | Value |
| ------ | ----- |
| Time   | O(n)  |
| Space  | O(1)  |

> Worst case: Element is at the last index or not present at all
> Best case: Element is at the first index

---

### 📘 **MCQs and Interview Questions**

---

#### ❓ Q1: When is **Linear Search** better than **Binary Search**?

✅ When the array is **unsorted** or **very small in size**.
Binary Search only works on **sorted arrays**.

---

#### ❓ Q2: What is the time complexity of Linear Search in the **worst case**?

* a) O(1)
* b) O(log n)
* ✅ **c) O(n)**
* d) O(n log n)

---

#### ❓ Q3: How would you modify linear search to return **all indices** of the target?

Use a `vector<int>` and store every match:

```cpp
vector<int> res;
for(int i = 0; i < nums.size(); i++) {
    if(nums[i] == target) {
        res.push_back(i);
    }
}
```

---

#### ❓ Q4: Can Linear Search be used on a Linked List?

✅ Yes!
Linked Lists can only be traversed sequentially, so **linear search is optimal** for them.

---

#### ❓ Q5: If multiple occurrences of the target exist, which one will Linear Search return?

✅ The **first occurrence** (lowest index).

---

### ✏️ **Theory-Based Question for Viva/Exams**

> **Q: What are the advantages and disadvantages of Linear Search?**

**Advantages:**

* Simple to implement
* Works on both **sorted and unsorted** arrays
* No need for preprocessing

**Disadvantages:**

* Slow on large datasets (O(n))
* Inefficient compared to binary search for sorted arrays

---

### 🔍 **Practical Use-Cases**

* Searching for a word in a **word puzzle**
* Finding a name in an **unsorted guest list**
* Checking for duplicates in small datasets

---

### ✅ Summary

| Feature             | Value                    |
| ------------------- | ------------------------ |
| Search Type         | Sequential (one by one)  |
| Works on            | Unsorted and sorted data |
| Time Complexity     | O(n)                     |
| Space Complexity    | O(1)                     |
| First Match Returns | Yes                      |

---
