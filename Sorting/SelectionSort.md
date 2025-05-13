
---

## 📘 Selection Sort

### 🔍 **Concept**

Selection Sort is a **comparison-based sorting algorithm** that repeatedly finds the **minimum (or maximum)** element from the **unsorted part** and puts it at the **beginning (or end)** of the sorted part.

It maintains two subarrays in the given array:

* The **sorted part** (initially empty).
* The **unsorted part** (initially the entire array).

### 🔄 **Algorithm Steps**

1. Start from the first element.
2. Find the **minimum** element in the unsorted part of the array.
3. Swap it with the **first element** of the unsorted part.
4. Move the boundary of the sorted part by one position to the right.
5. Repeat until the array is fully sorted.

---

### 🧠 **Pseudocode**

```
for i = 0 to n-2:
    minIndex = i
    for j = i+1 to n-1:
        if arr[j] < arr[minIndex]:
            minIndex = j
    swap arr[i] and arr[minIndex]
```

---

### 💻 **C++ Code**

```cpp
#include <iostream>
using namespace std;

void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int minIndex = i;

        // Find the index of the minimum element in unsorted part
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex])
                minIndex = j;
        }

        // Swap minimum element with the first element of unsorted part
        swap(arr[i], arr[minIndex]);
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {64, 25, 12, 22, 11};
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

### 🧮 **Dry Run (Example)**

**Input**: `[64, 25, 12, 22, 11]`

#### Iteration 1:

* Minimum from index 0–4: `11`
* Swap with `64`
* Array: `[11, 25, 12, 22, 64]`

#### Iteration 2:

* Minimum from index 1–4: `12`
* Swap with `25`
* Array: `[11, 12, 25, 22, 64]`

#### Iteration 3:

* Minimum from index 2–4: `22`
* Swap with `25`
* Array: `[11, 12, 22, 25, 64]`

#### Iteration 4:

* Minimum from index 3–4: `25` (already in place)
* Final Array: `[11, 12, 22, 25, 64]`

---

### 📊 Time and Space Complexity

| Case       | Comparisons | Swaps | Time Complexity |
| ---------- | ----------- | ----- | --------------- |
| Best Case  | O(n²)       | O(n)  | O(n²)           |
| Average    | O(n²)       | O(n)  | O(n²)           |
| Worst Case | O(n²)       | O(n)  | O(n²)           |
| Space      | -           | -     | O(1) (in-place) |

---

### ✅ **Key Points**

* **Not stable**: May change relative order of equal elements.
* **In-place algorithm**: No extra space needed.
* Performs **minimum number of swaps** among all sorting algorithms (at most **n-1**).
* **Inefficient** for large datasets due to O(n²) time complexity.

---
