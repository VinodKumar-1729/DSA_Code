

## ✅ **Selection Sort**

---

### 🧩 **Problem Statement**

> **Given** an array of `n` elements, sort the array in **ascending order** using the **Selection Sort** algorithm.
>
> You are not allowed to use built-in sort functions.
> Return or print the sorted array.

---

### 💡 **Concept: What is Selection Sort?**

* Selection Sort is a **comparison-based sorting algorithm**.
* It works by **dividing the array** into two parts:

  * **Sorted** part (at the beginning)
  * **Unsorted** part (rest of the array)
* In every pass:

  1. **Find the minimum element** in the unsorted part.
  2. **Swap it with the first element** of the unsorted part.
* Repeat this process until the array is fully sorted.

🟢 **Key Points**:

* It **always takes O(n²) time** (even for sorted arrays).
* **In-place** (no extra space used).
* **Not stable** by default.

---

### 🔁 **Dry Run Example**

Let’s take:
`arr = [29, 10, 14, 37, 13]`

#### **Pass 1 (i=0):**

* Min in \[29,10,14,37,13] → 10
* Swap 10 and 29 → `[10, 29, 14, 37, 13]`

#### **Pass 2 (i=1):**

* Min in \[29,14,37,13] → 13
* Swap 13 and 29 → `[10, 13, 14, 37, 29]`

#### **Pass 3 (i=2):**

* Min in \[14,37,29] → 14 (no swap needed)

#### **Pass 4 (i=3):**

* Min in \[37,29] → 29
* Swap 29 and 37 → `[10, 13, 14, 29, 37]`

#### **Pass 5 (i=4):**

* Already sorted

🔚 Final array: `[10, 13, 14, 29, 37]`

---

### 💻 **C++ Code: Selection Sort**

```cpp
#include <iostream>
using namespace std;

void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; ++i) {
        int minIndex = i;

        // Find index of minimum element in unsorted part
        for (int j = i + 1; j < n; ++j) {
            if (arr[j] < arr[minIndex])
                minIndex = j;
        }

        // Swap the found minimum with the first element of unsorted part
        if (minIndex != i) {
            int temp = arr[i];
            arr[i] = arr[minIndex];
            arr[minIndex] = temp;
        }
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; ++i)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {29, 10, 14, 37, 13};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    printArray(arr, n);

    selectionSort(arr, n);

    cout << "Sorted array: ";
    printArray(arr, n);

    return 0;
}
```

---

### ❓ **Common Exam & Interview Questions**

---

#### ✅ **Q1. What is the time complexity of Selection Sort?**

| Case       | Time Complexity |
| ---------- | --------------- |
| Best Case  | O(n²)           |
| Average    | O(n²)           |
| Worst Case | O(n²)           |

> ❗ It **does not change** even if the array is already sorted.

---

#### ✅ **Q2. What is the space complexity?**

* O(1) – It’s an **in-place sorting algorithm**.

---

#### ✅ **Q3. Is selection sort stable?**

* ❌ **Not stable by default**.
* Because swapping non-adjacent elements can disturb the relative order of equal elements.

🧠 *Example*:
Input: `[(3, A), (3, B), (1, C)]`
After sorting: `[(1, C), (3, B), (3, A)]`
Order of (3, A) and (3, B) is changed.

---

#### ✅ **Q4. Can selection sort be made stable?**

* Yes, by **inserting** the minimum instead of swapping (like in Insertion Sort), but it increases the number of moves.

---

#### ✅ **Q5. When should you use Selection Sort?**

Use it when:

* **Memory write is expensive**, since it makes **only (n - 1) swaps**.
* You’re dealing with **small datasets**.

---

#### ✅ **Q6. Compare Selection Sort vs Bubble Sort.**

| Feature      | Selection Sort | Bubble Sort       |
| ------------ | -------------- | ----------------- |
| Time (Best)  | O(n²)          | O(n) (with opt.)  |
| Time (Worst) | O(n²)          | O(n²)             |
| Stability    | Not stable     | Stable            |
| Swaps        | ≤ (n - 1)      | Many              |
| Comparisons  | O(n²)          | O(n²)             |
| Adaptiveness | ❌ Not adaptive | ✅ Yes (optimized) |

---

#### ✅ **Q7. What is the number of comparisons and swaps in Selection Sort?**

* **Comparisons:**
  `n*(n-1)/2` ≈ O(n²)
* **Swaps:**
  At most `n - 1` swaps → efficient when writing to memory is costly.

---

### 📘 Summary Sheet for Quick Revision

| Feature          | Value                    |
| ---------------- | ------------------------ |
| Type             | Comparison-based sorting |
| Time Complexity  | O(n²)                    |
| Space Complexity | O(1)                     |
| Stable           | ❌ No                     |
| In-place         | ✅ Yes                    |
| Adaptive         | ❌ No                     |
| Number of Swaps  | O(n) (at most n - 1)     |

---
