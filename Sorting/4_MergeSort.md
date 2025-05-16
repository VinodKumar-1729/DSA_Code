

## ✅ **Merge Sort – Complete Notes (C++)**

---

### 🧩 **Problem Statement**

> **Given** an array of `n` integers, sort the array in **ascending order** using **Merge Sort**.
>
> Do not use built-in sort functions. Return or print the sorted array.

---

### 💡 **Concept: What is Merge Sort?**

* **Merge Sort** is a **divide-and-conquer** algorithm.
* It works by:

  1. **Dividing** the array into two halves.
  2. **Recursively sorting** both halves.
  3. **Merging** the two sorted halves into one.

✅ The merge step is where the actual sorting happens.

---

### 🔁 **Dry Run Example**

Input: `arr = [38, 27, 43, 3, 9, 82, 10]`

**Step-by-step division:**

```
[38, 27, 43, 3, 9, 82, 10]
=> Divide into:
[38, 27, 43] and [3, 9, 82, 10]

Further divide:
[38, 27, 43] => [38], [27, 43] => [38], [27], [43]
[3, 9, 82, 10] => [3, 9], [82, 10] => [3], [9], [82], [10]
```

**Step-by-step merging:**

```
Merge: [27] + [43] → [27, 43]
Merge: [38] + [27, 43] → [27, 38, 43]

Merge: [3] + [9] → [3, 9]
Merge: [82] + [10] → [10, 82]
Merge: [3, 9] + [10, 82] → [3, 9, 10, 82]

Final merge: [27, 38, 43] + [3, 9, 10, 82] → [3, 9, 10, 27, 38, 43, 82]
```

---

### 💻 **C++ Code: Merge Sort**

```cpp
#include <iostream>
using namespace std;

void merge(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;

    // Temporary arrays
    int L[n1], R[n2];

    // Copy data
    for (int i = 0; i < n1; i++)
        L[i] = arr[left + i];
    for (int j = 0; j < n2; j++)
        R[j] = arr[mid + 1 + j];

    // Merge the arrays
    int i = 0, j = 0, k = left;

    while (i < n1 && j < n2) {
        if (L[i] <= R[j])
            arr[k++] = L[i++];
        else
            arr[k++] = R[j++];
    }

    // Copy remaining elements
    while (i < n1)
        arr[k++] = L[i++];
    while (j < n2)
        arr[k++] = R[j++];
}

void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;

        // Sort halves
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        // Merge sorted halves
        merge(arr, left, mid, right);
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; ++i)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {38, 27, 43, 3, 9, 82, 10};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    printArray(arr, n);

    mergeSort(arr, 0, n - 1);

    cout << "Sorted array: ";
    printArray(arr, n);

    return 0;
}
```

---

### 🎯 **Key Points**

| Property       | Value                |
| -------------- | -------------------- |
| Algorithm Type | Divide and Conquer   |
| In-place       | ❌ (uses extra space) |
| Stable         | ✅ Yes                |
| Adaptive       | ❌ No                 |

---

### 📊 **Time & Space Complexity**

| Case       | Time Complexity | Explanation                     |
| ---------- | --------------- | ------------------------------- |
| Best Case  | O(n log n)      | Always divides in log n levels  |
| Average    | O(n log n)      | Same as best                    |
| Worst Case | O(n log n)      | Even in reversed arrays         |
| Space      | O(n)            | Uses extra space during merging |

---

### ❓ **Interview & Exam Questions**

---

#### ✅ Q1. **Why is Merge Sort not in-place?**

Because it uses **temporary arrays** to hold elements while merging. So, additional O(n) space is used.

---

#### ✅ Q2. **Is Merge Sort stable? Why or why not?**

Yes, it is **stable**. During merging, if elements are equal, it keeps the **original order** of elements.

🧠 Example:
`[(5, A), (5, B)] → After merge: [(5, A), (5, B)]`

---

#### ✅ Q3. **Why is Merge Sort preferred for Linked Lists?**

* No extra space is needed.
* Random access is not required.
* Merge sort easily splits and merges linked lists using pointers.

---

#### ✅ Q4. **Why is Merge Sort better than Quick Sort in some cases?**

* For **large data stored in external memory (like disk)**, Merge Sort is better because:

  * It accesses data sequentially.
  * It’s **stable**, while Quick Sort is not.

---

#### ✅ Q5. **What is the best sorting algorithm for large datasets?**

* **Merge Sort** is good for large datasets or files stored on disk.
* Time complexity remains **O(n log n)** even in the worst case.

---

### 📌 **Comparison Table**

| Sorting Algo | Time (Best) | Time (Worst) | Space    | Stable | In-place |
| ------------ | ----------- | ------------ | -------- | ------ | -------- |
| Bubble Sort  | O(n)        | O(n²)        | O(1)     | ✅ Yes  | ✅        |
| Insertion    | O(n)        | O(n²)        | O(1)     | ✅ Yes  | ✅        |
| Merge Sort   | O(n log n)  | O(n log n)   | O(n)     | ✅ Yes  | ❌        |
| Quick Sort   | O(n log n)  | O(n²)        | O(log n) | ❌ No   | ✅        |

---

### 📝 **MCQ Practice**

1. **What is the time complexity of Merge Sort in worst case?**
   a) O(n)
   b) O(n log n)
   c) O(n²)
   d) O(log n)
   ✅ **Answer: b**

2. **Is Merge Sort suitable for linked lists?**
   a) No
   b) Yes
   ✅ **Answer: b**

3. **What is the space complexity of Merge Sort?**
   a) O(1)
   b) O(log n)
   c) O(n)
   ✅ **Answer: c**

---

### ✅ Summary

* 🔹 **Divide & Conquer** method
* 🔹 Always **O(n log n)** time
* 🔹 Requires **extra space (O(n))**
* 🔹 Used in **external sorting, linked lists**
* 🔹 **Stable**, **not in-place**

---
