

## ✅ **Bubble Sort**

---

### 🧩 **Problem Statement**

> **Given** an array of `n` integers, **sort the array in ascending order** using the **Bubble Sort** algorithm.
>
> Do not use built-in sorting functions.
> Return or print the sorted array.

---

### 💡 **Concept: What is Bubble Sort?**

* **Bubble Sort** is a simple **comparison-based sorting algorithm**.
* It works by **repeatedly swapping adjacent elements** if they are in the wrong order.
* After each pass, the **largest unsorted element "bubbles" to the end** of the array.
* The process continues until the array is sorted.

---

### 🔁 **Dry Run Example**

Input: `arr = [5, 1, 4, 2, 8]`

Let’s walk through the passes:

| Pass | Comparisons        | Swaps                       | Result |
| ---- | ------------------ | --------------------------- | ------ |
| 1    | 5>1, 5>4, 5>2, 8>2 | \[1, 4, 2, 5, 8]            |        |
| 2    | 1<4, 4>2, 5<8      | \[1, 2, 4, 5, 8]            |        |
| 3    | 1<2, 2<4, 4<5      | \[1, 2, 4, 5, 8] (No swaps) |        |

✅ Early termination possible when **no swaps** in a pass.

---

### 💻 **C++ Code: Bubble Sort**

```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    bool swapped;

    for (int i = 0; i < n - 1; ++i) {
        swapped = false;

        // Last i elements are already in place
        for (int j = 0; j < n - i - 1; ++j) {
            if (arr[j] > arr[j + 1]) {
                // Swap if elements are in wrong order
                swap(arr[j], arr[j + 1]);
                swapped = true;
            }
        }

        // If no elements were swapped in the inner loop, the array is sorted
        if (!swapped)
            break;
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; ++i)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {5, 1, 4, 2, 8};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    printArray(arr, n);

    bubbleSort(arr, n);

    cout << "Sorted array: ";
    printArray(arr, n);

    return 0;
}
```

---

### ❓ **Common Questions & Interview-Focused Insights**

---

#### ✅ **Q1. What is the time complexity of Bubble Sort?**

| Case       | Time Complexity | Explanation                              |
| ---------- | --------------- | ---------------------------------------- |
| Best Case  | O(n)            | When array is already sorted (optimized) |
| Average    | O(n²)           | General unsorted input                   |
| Worst Case | O(n²)           | Reversed array                           |

---

#### ✅ **Q2. What is the space complexity?**

* O(1) – Uses **no extra space** (in-place sorting).

---

#### ✅ **Q3. Is Bubble Sort stable?**

* ✅ **Yes**
* Equal elements retain their **relative order**.

🧠 Example:
Input: `[(3, A), (3, B)]` → After sorting: `[(3, A), (3, B)]`

---

#### ✅ **Q4. Is Bubble Sort adaptive?**

* ✅ **Yes (if optimized)**
* Stops early if no swaps were made in a pass → saves unnecessary iterations.

---

#### ✅ **Q5. When to use Bubble Sort?**

Use it:

* For **learning purposes**.
* When the input array is **small** and/or **mostly sorted**.
* For **educational environments**, not real-world applications.

---

#### ✅ **Q6. What if you don’t use the “swapped” optimization?**

* Even if the array is sorted, it will do all `n-1` passes.
* Time complexity in best case will be O(n²).

✅ With swapped check → best case becomes O(n).

---

#### ✅ **Q7. Compare Bubble Sort vs Insertion Sort**

| Feature        | Bubble Sort      | Insertion Sort      |
| -------------- | ---------------- | ------------------- |
| Time (Best)    | O(n) (optimized) | O(n)                |
| Time (Worst)   | O(n²)            | O(n²)               |
| Space          | O(1)             | O(1)                |
| Stable         | ✅ Yes            | ✅ Yes               |
| Adaptive       | ✅ (if optimized) | ✅ Yes               |
| Real use cases | Very limited     | Used in small lists |

---

### 📝 **Summary Table**

| Feature          | Value                        |
| ---------------- | ---------------------------- |
| Sorting Type     | Comparison Sort              |
| Time Complexity  | Best: O(n), Worst: O(n²)     |
| Space Complexity | O(1)                         |
| In-place         | ✅ Yes                        |
| Stable           | ✅ Yes                        |
| Adaptive         | ✅ Yes (with optimization)    |
| Recommended Use  | Learning/educational purpose |

---

### 🔍 Optional MCQ Practice (Sample)

1. **Which of the following is TRUE about Bubble Sort?**
   a) It always takes O(n²) time
   b) It is not stable
   c) It can be optimized for best case O(n)
   d) It uses O(n) extra space
   ✅ **Answer: c**

2. **What is the maximum number of swaps in Bubble Sort (worst case)?**
   a) n
   b) n-1
   c) n²
   d) n(n-1)/2
   ✅ **Answer: d**

---
