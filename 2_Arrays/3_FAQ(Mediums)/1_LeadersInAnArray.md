

## 📘 **Leaders in an Array – Full Notes**

---

### 🔍 **Definition**

In an array, a **leader** is an element that is **strictly greater than all the elements to its right**.

> ✅ The **rightmost element** is always a leader.

---

### 🧠 **Key Concepts**

* Leaders help identify dominant values in sequences.
* Useful in problems involving **future greater elements**, stock span, etc.
* Related to **reverse traversal** and **comparative analysis**.

---

### 📊 **Example**

```cpp
Input:  [16, 17, 4, 3, 5, 2]
Output: [17, 5, 2]
```

**Explanation:**

* From right to left:

  * 2 → Leader (no elements to the right)
  * 5 > 2 → Leader
  * 3 < 5 → Not a leader
  * 4 < 5 → Not a leader
  * 17 > all → Leader
  * 16 < 17 → Not a leader

---

### ⚙️ **C++ Code Explanation**

```cpp
class Solution {
public:
    vector<int> leaders(vector<int>& nums) {
        int n = nums.size();
        vector<int> leaders;

        if (n < 1) {
            return leaders;
        }

        // Step 1: Last element is always a leader
        leaders.push_back(nums[n - 1]);
        int curLeader = nums[n - 1];

        // Step 2: Traverse from right to left
        for (int i = n - 2; i >= 0; i--) {
            if (nums[i] > curLeader) {
                curLeader = nums[i];
                leaders.push_back(nums[i]);
            }
        }

        // Step 3: Reverse to maintain original order
        int start = 0, end = leaders.size() - 1;
        while (start < end) {
            swap(leaders[start], leaders[end]);
            start++;
            end--;
        }

        return leaders;
    }
};
```

---

### ⏱️ **Time & Space Complexity**

* **Time Complexity:** `O(n)` – single pass from right to left + reverse.
* **Space Complexity:** `O(k)` – where `k` is the number of leaders (extra array used).

---

### 🔁 **Alternate Approaches**

1. **Brute Force (Nested Loops)**:

   * Compare each element with all to its right.
   * **Time:** `O(n^2)`

2. **Stack-Based Method (optional variant)**:

   * Can use a stack in reverse order to push only leaders.

---

## 🎯 Use Cases in Real Life

* Stock markets: Finding dominant prices.
* Sales: Highest sale after a point in time.
* Trend analysis: Peaks in reverse chronological data.

---

## 🎓 **Exam Questions with Answers**

---

### ✅ **Q1: What is a Leader in an Array?**

**Answer:** An element is a leader if it is **strictly greater than all elements to its right**.

---

### ✅ **Q2: What is the Time Complexity of the Optimal Solution?**

**Answer:** The optimal solution works in `O(n)` time due to single reverse traversal and optional reversing of the result list.

---

### ✅ **Q3: Is the last element of the array always a leader? Why?**

**Answer:** Yes, because there are no elements to its right, so it's trivially greater.

---

### ✅ **Q4: Give an example input and output for Leaders in an Array.**

**Input:** `[7, 10, 4, 10, 6, 5, 2]`
**Output:** `[10, 6, 5, 2]`

---

### ✅ **Q5: Can duplicate values be leaders?**

**Answer:** Only the **first occurrence from the right** is considered if it's greater than all elements to the right. Equality doesn't qualify.

---

## 💼 **Interview Questions with Suggested Answers**

---

### 💬 **Q1: How would you find leaders in an array of 1 million integers efficiently?**

**Answer:** I would use the reverse traversal method in `O(n)` time by maintaining a current leader and updating only when I find a larger element.

---

### 💬 **Q2: Can we do this without using extra space?**

**Answer:** Yes, we can print the leaders directly during reverse traversal instead of storing them, if output array is not mandatory.

---

### 💬 **Q3: How would you modify the code to handle negative numbers and duplicates?**

**Answer:** The same logic works for negative numbers. For duplicates, only elements that are **strictly greater** than `curLeader` qualify, so adjust condition accordingly (`nums[i] >= curLeader` if duplicates are allowed as leaders).

---

### 💬 **Q4: How would you find leaders if the array is coming as a stream?**

**Answer:** In a stream, we can only determine leaders after reading the entire array, unless we have **future insight**, so we’d buffer the stream and then apply the reverse traversal logic.

---

## 🧾 Summary

* Leaders = values greater than all elements to their right.
* Use reverse traversal and maintain a current max.
* Time-efficient approach: O(n)
* Common in exams and interviews for array problems.

---
