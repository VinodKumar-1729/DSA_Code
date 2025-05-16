
## ✅ **Quick Sort – Complete Notes (C++)**

---

### 🧩 **Problem Statement**

> **Given** an array of `n` integers, sort the array in **ascending order** using **Quick Sort**.
>
> Implement the algorithm from scratch without using any built-in sort function.

---

### 💡 **Concept: What is Quick Sort?**

* **Quick Sort** is a **Divide-and-Conquer** sorting algorithm.
* It works by:

  1. Choosing a **pivot** element.
  2. **Partitioning** the array such that:

     * All elements less than pivot go to left.
     * All elements greater than pivot go to right.
  3. Recursively sorting the **left and right sub-arrays**.

✅ Quick Sort is **in-place** and often faster than Merge Sort in practice.

---

### 🔁 **Dry Run Example**

Input: `arr = [10, 7, 8, 9, 1, 5]`
Let’s use the **last element as pivot**.

```
Initial array: [10, 7, 8, 9, 1, 5]
Pivot = 5

→ Partition step:
   After partition: [1, 5, 8, 9, 10, 7]
   Pivot index = 1

→ Left sub-array: [1] → already sorted
→ Right sub-array: [8, 9, 10, 7]
   Pivot = 7
   After partition: [1, 5, 7, 9, 10, 8]
   Pivot index = 2

Continue partitioning recursively...
Final sorted array: [1, 5, 7, 8, 9, 10]
```

---

### 💻 **C++ Code: Quick Sort**

```cpp
#include <iostream>
using namespace std;

// Partition function using last element as pivot
int partition(int arr[], int low, int high) {
    int pivot = arr[high]; // pivot
    int i = low - 1;        // index of smaller element

    for (int j = low; j < high; j++) {
        // If current element <= pivot
        if (arr[j] <= pivot) {
            i++;
            swap(arr[i], arr[j]); // swap
        }
    }

    // Swap pivot to correct position
    swap(arr[i + 1], arr[high]);
    return (i + 1);
}

// QuickSort function
void quickSort(int arr[], int low, int high) {
    if (low < high) {
        // pi is partitioning index
        int pi = partition(arr, low, high);

        // Recursively sort elements
        quickSort(arr, low, pi - 1);  // left
        quickSort(arr, pi + 1, high); // right
    }
}

// Utility to print array
void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
}

// Main driver code
int main() {
    int arr[] = {10, 7, 8, 9, 1, 5};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    printArray(arr, n);

    quickSort(arr, 0, n - 1);

    cout << "Sorted array: ";
    printArray(arr, n);

    return 0;
}
```

---

### 📊 **Time & Space Complexity**

| Case       | Time Complexity | Explanation                       |
| ---------- | --------------- | --------------------------------- |
| Best Case  | O(n log n)      | Balanced partitioning             |
| Average    | O(n log n)      | Randomized pivot gives balance    |
| Worst Case | O(n²)           | Already sorted (if bad pivot)     |
| Space      | O(log n)        | Due to recursion stack (in-place) |

---

### 🎯 **Key Characteristics**

| Property      | Value                            |
| ------------- | -------------------------------- |
| Type          | Divide & Conquer                 |
| In-place      | ✅ Yes                            |
| Stable        | ❌ No                             |
| Adaptive      | ❌ No                             |
| Extra Space   | O(log n) recursion stack         |
| Preferred for | Arrays and high-performance apps |

---

### ❓ **Interview & Exam Questions**

---

#### ✅ Q1. **What is the worst-case time complexity of Quick Sort?**

* **O(n²)**, when the pivot selection causes unbalanced partitions (e.g., sorted/reverse sorted arrays).

---

#### ✅ Q2. **How to avoid the worst-case in Quick Sort?**

* Use **randomized pivot** or **median-of-three** pivot strategy to balance partitioning.

---

#### ✅ Q3. **Is Quick Sort stable? Why or why not?**

* No, it’s **not stable**.
* It may **swap equal elements**, disturbing original order.

🧠 Example:
`(5, A), (5, B)` could become `(5, B), (5, A)`

---

#### ✅ Q4. **Why is Quick Sort better than Merge Sort in practice?**

* Faster due to **in-place sorting** (less memory).
* Better **cache performance** (sequential memory access).
* **Tail recursion optimization** possible.

---

#### ✅ Q5. **Where is Quick Sort not recommended?**

* On **linked lists** (because partitioning needs random access).
* For **large datasets stored on disk**, where Merge Sort is preferred.

---

### 📌 **Comparison Table**

| Algorithm   | Time (Best) | Time (Worst) | Space    | Stable | In-place |
| ----------- | ----------- | ------------ | -------- | ------ | -------- |
| Quick Sort  | O(n log n)  | O(n²)        | O(log n) | ❌      | ✅        |
| Merge Sort  | O(n log n)  | O(n log n)   | O(n)     | ✅      | ❌        |
| Insertion   | O(n)        | O(n²)        | O(1)     | ✅      | ✅        |
| Bubble Sort | O(n)        | O(n²)        | O(1)     | ✅      | ✅        |

---

### 📝 **MCQ Practice**

1. **Quick Sort is based on which technique?**
   a) Dynamic Programming
   b) Greedy
   c) Divide and Conquer
   ✅ **Answer: c**

2. **What is the average time complexity of Quick Sort?**
   a) O(n²)
   b) O(n log n)
   ✅ **Answer: b**

3. **Is Quick Sort a stable sort?**
   a) Yes
   b) No
   ✅ **Answer: b**

4. **Which sorting algorithm is best for large in-memory arrays?**
   a) Merge Sort
   b) Insertion Sort
   c) Quick Sort
   ✅ **Answer: c**

---

### ✅ Summary

* 🔹 Quick Sort is fast and efficient in most cases.
* 🔹 Can degrade to O(n²) without good pivot strategy.
* 🔹 Best suited for in-memory sorting and arrays.
* 🔹 Not stable, but in-place and highly cache-efficient.

---
