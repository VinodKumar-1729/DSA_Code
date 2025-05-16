
## ✅ **Insertion Sort**

---

### 🧩 **Problem Statement**

> **Given** an array of `n` integers, sort the array in **ascending order** using the **Insertion Sort** algorithm.
>
> Do not use built-in sorting functions.
> Return or print the sorted array.

---

### 💡 **Concept: What is Insertion Sort?**

* Insertion Sort is a **simple comparison-based sorting algorithm**.
* It builds the final sorted array **one element at a time**.
* Similar to how you sort playing cards in your hand:

  * You pick the next card and insert it at the correct position in the sorted portion of the hand.

🧠 **Working Principle**:

* Assume the first element is already sorted.
* Take the next element and compare it with all elements in the sorted part (left side).
* **Shift** elements greater than the current element to the right.
* **Insert** the current element into its correct position.

---

### 🔁 **Dry Run Example**

Input: `arr = [5, 2, 4, 6, 1, 3]`

We start from the second element (i = 1):

| Pass | Key | Array After Pass                |
| ---- | --- | ------------------------------- |
| 1    | 2   | \[2, 5, 4, 6, 1, 3]             |
| 2    | 4   | \[2, 4, 5, 6, 1, 3]             |
| 3    | 6   | \[2, 4, 5, 6, 1, 3] (no change) |
| 4    | 1   | \[1, 2, 4, 5, 6, 3]             |
| 5    | 3   | \[1, 2, 3, 4, 5, 6]             |

Final Output: `[1, 2, 3, 4, 5, 6]`

---

### 💻 **C++ Code: Insertion Sort**

```cpp
#include <iostream>
using namespace std;

void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; ++i) {
        int key = arr[i];       // element to be inserted
        int j = i - 1;

        // Move elements greater than key to one position ahead
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }

        // Insert the key at the correct position
        arr[j + 1] = key;
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; ++i)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {5, 2, 4, 6, 1, 3};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    printArray(arr, n);

    insertionSort(arr, n);

    cout << "Sorted array: ";
    printArray(arr, n);

    return 0;
}
```

---

### ❓ **Common Questions & Interview Insights**

---

#### ✅ **Q1. What is the time complexity of Insertion Sort?**

| Case       | Time Complexity | Explanation             |
| ---------- | --------------- | ----------------------- |
| Best Case  | O(n)            | Array is already sorted |
| Average    | O(n²)           | Random order            |
| Worst Case | O(n²)           | Array sorted in reverse |

---

#### ✅ **Q2. What is the space complexity?**

* O(1) – In-place sorting, no extra memory used.

---

#### ✅ **Q3. Is Insertion Sort stable?**

* ✅ **Yes**
* Equal elements retain their **original relative order**.

🧠 Example:
Input: `[(2, A), (2, B), (1, C)]`
After sorting: `[(1, C), (2, A), (2, B)]`

---

#### ✅ **Q4. Is Insertion Sort adaptive?**

* ✅ Yes
* Performs better when input is **partially sorted**.
* Best case: **O(n)** when array is already sorted.

---

#### ✅ **Q5. When should you use Insertion Sort?**

Use it when:

* Array size is **small**.
* Array is **almost sorted**.
* You need a **stable** and **adaptive** algorithm.

---

#### ✅ **Q6. Compare Insertion Sort vs Selection Sort**

| Feature      | Insertion Sort | Selection Sort      |
| ------------ | -------------- | ------------------- |
| Time (Best)  | O(n)           | O(n²)               |
| Time (Worst) | O(n²)          | O(n²)               |
| Space        | O(1)           | O(1)                |
| Stability    | ✅ Stable       | ❌ Not stable        |
| Adaptive     | ✅ Yes          | ❌ No                |
| Swaps/Moves  | More (shifts)  | Fewer (at most n-1) |

---

#### ✅ **Q7. How many comparisons and shifts in Insertion Sort?**

* In the **worst case**:

  * Comparisons: `n(n-1)/2` → O(n²)
  * Shifts: `n(n-1)/2` → O(n²)

But in the **best case (already sorted)**:

* Comparisons: `n-1`
* Shifts: `0`

---

### 📝 **Summary Table**

| Feature          | Value                            |
| ---------------- | -------------------------------- |
| Type             | Comparison Sort                  |
| Time Complexity  | O(n²), Best: O(n)                |
| Space Complexity | O(1)                             |
| Stability        | ✅ Yes                            |
| Adaptive         | ✅ Yes                            |
| In-place         | ✅ Yes                            |
| Practical Usage  | Small or partially sorted arrays |

---
