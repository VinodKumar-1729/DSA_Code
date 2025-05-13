
---

## 📘 Bubble Sort 

### 🔍 **Concept**

Bubble Sort is a simple **comparison-based** sorting algorithm. It repeatedly **swaps adjacent elements** if they are in the wrong order. This process **"bubbles"** the largest (or smallest) element to its correct position in each iteration.

It’s called “bubble” sort because smaller elements slowly **"bubble up"** to the top (beginning) of the array with each pass.

---

### 🔄 **Algorithm Steps**

1. Traverse the array from start to end.
2. Compare each pair of adjacent elements.
3. Swap them if they are in the wrong order.
4. After each pass, the largest unsorted element reaches its correct position.
5. Repeat for all elements until the array is sorted.

---

### 🧠 **Pseudocode**

```
for i = 0 to n-1:
    for j = 0 to n-i-2:
        if arr[j] > arr[j+1]:
            swap arr[j], arr[j+1]
```

---

### 💻 **C++ Code**

```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    bool swapped;
    for (int i = 0; i < n - 1; i++) {
        swapped = false;

        // Traverse the array till the unsorted part
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
                swapped = true;
            }
        }

        // If no two elements were swapped in the inner loop, break
        if (!swapped)
            break;
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
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

### 🧮 **Dry Run Example**

**Input**: `[64, 34, 25, 12, 22, 11, 90]`

#### Pass 1:

* Swap 64 and 34 → `[34, 64, 25, 12, 22, 11, 90]`
* Swap 64 and 25 → `[34, 25, 64, 12, 22, 11, 90]`
* Swap 64 and 12 → `[34, 25, 12, 64, 22, 11, 90]`
* ...
* 90 moves to the end

#### Pass 2:

* Largest of remaining elements moves to second-last position

...

Continue until no swaps needed.

---

### 📊 Time and Space Complexity

| Case       | Comparisons | Swaps | Time Complexity  |
| ---------- | ----------- | ----- | ---------------- |
| Best Case  | O(n)        | 0     | O(n) (optimized) |
| Average    | O(n²)       | O(n²) | O(n²)            |
| Worst Case | O(n²)       | O(n²) | O(n²)            |
| Space      | -           | -     | O(1) (in-place)  |

---

### ✅ **Key Points**

* **Stable** sort: Maintains relative order of equal elements.
* **In-place**: No extra memory used.
* **Easy to understand** and implement.
* **Inefficient** on large datasets.
* Optimized version stops early if array becomes sorted before all passes.

---
