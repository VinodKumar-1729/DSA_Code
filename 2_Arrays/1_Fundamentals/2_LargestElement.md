
## 📘 Linear Search: Finding the Largest Element in an Array (C++)

---

### 📌 Problem Statement

> Given an array `nums[]` of integers, find and return the **largest (maximum) element** using **linear search**.
> You are not allowed to use STL functions like `max_element()`.

---

### ✅ Example

```cpp
Input: nums = {3, 7, 1, 9, 5}
Output: 9
Explanation: 9 is the largest number in the array.
```

---

### 💡 Concept

* The goal is to **traverse** the array **once** and keep track of the largest value found so far.
* This is a **variant of linear search**, where instead of searching for a match, you search for the **maximum value**.
* Start with the **first element** as the largest and then compare each element with it.

---

### 🔁 Dry Run

Let’s take `nums = {8, 12, 3, 20, 5}`

| Step | i | nums\[i] | largest (before) | Comparison | largest (after) |
| ---- | - | -------- | ---------------- | ---------- | --------------- |
| 1    | 1 | 12       | 8                | 12 > 8 ✅   | 12              |
| 2    | 2 | 3        | 12               | 3 > 12 ❌   | 12              |
| 3    | 3 | 20       | 12               | 20 > 12 ✅  | 20              |
| 4    | 4 | 5        | 20               | 5 > 20 ❌   | 20              |

✅ Final Output: 20

---

### 💻 C++ Code (Your Code — Correct and Clean)

```cpp
class Solution {
public:
    int largestElement(vector<int>& nums) {
        int n = nums.size();
        int largest = nums[0]; // Start by assuming the first element is the largest
        for(int i = 1; i < n; i++) {
            if(nums[i] > largest) {
                largest = nums[i]; // Update if current element is larger
            }
        }
        return largest; // Return the largest value found
    }
};
```

---

### ⏱️ Time and Space Complexity

| Metric | Value |
| ------ | ----- |
| Time   | O(n)  |
| Space  | O(1)  |

✅ Efficient: Only one pass through the array, constant space.

---

### 🧠 Questions & Answers (Exam + Interview Focus)

---

#### ❓ Q1: What is the best and worst-case time complexity of this algorithm?

✅ **Best, Worst, and Average Case = O(n)**
Because we have to check every element at least once.

---

#### ❓ Q2: Can you find the largest and smallest element in a single pass?

Yes. You can do:

```cpp
int largest = nums[0], smallest = nums[0];
for(int i = 1; i < nums.size(); i++) {
    if(nums[i] > largest) largest = nums[i];
    if(nums[i] < smallest) smallest = nums[i];
}
```

---

#### ❓ Q3: Is it necessary to initialize `largest = nums[0]`?

✅ Yes. This ensures the algorithm works for arrays containing **all negative** numbers or **single elements**.

---

#### ❓ Q4: What if the array is empty?

You must handle this case:

```cpp
if(nums.empty()) return INT_MIN; // Or throw an exception
```

---

#### ❓ Q5: Why not sort the array and return the last element?

* Sorting takes O(n log n) time.
* Our linear search approach is **faster (O(n))** and does not modify the array.

---

### 📚 Theory/Concept Questions (Viva & MCQ)

---

#### ❓ Linear Search is:

* a) Only used for searching fixed values
* ✅ b) A way to check all elements linearly
* c) Only for sorted arrays
* d) None of the above

---

#### ❓ Which approach gives the best performance to find the largest element?

✅ **Single traversal (O(n))**
Sorting is overkill unless needed for other operations.

---

### ✅ Summary

| Feature               | Value                         |
| --------------------- | ----------------------------- |
| Search Type           | Sequential                    |
| Applicable On         | Sorted/Unsorted Arrays        |
| Use Case              | Find max value in O(n) time   |
| Time Complexity       | O(n)                          |
| Space Complexity      | O(1)                          |
| Best for Small/Large? | Best for all (no sort needed) |

---

### ✨ Extra Practice

Try modifying the code to:

* Return **index** of largest element
* Return **all indices** if there are duplicates of the max
* Work for **negative integers only**

---
