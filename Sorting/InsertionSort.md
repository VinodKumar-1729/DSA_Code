
---

## 📘 Insertion Sort – Notes

### 🔍 **Concept**

Insertion Sort builds the sorted array one element at a time by **comparing and inserting** the current element into its **correct position** among the already sorted part of the array.

Think of sorting playing cards in your hand: You pick one card at a time and insert it into the correct position among the already sorted cards.

---

### 🔄 **Algorithm Steps**

1. Start from the second element (index 1), treat it as the "key".
2. Compare it with the elements before it (sorted subarray).
3. Shift all elements greater than the key one position ahead.
4. Insert the key at the correct position.
5. Repeat for all elements.

---

### 🧠 **Pseudocode**

```
for i = 1 to n-1:
    key = arr[i]
    j = i - 1
    while j >= 0 and arr[j] > key:
        arr[j+1] = arr[j]
        j = j - 1
    arr[j+1] = key
```

---

### 💻 **Your C++ Code Explained**

```cpp
#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    vector<int> insertionSort(vector<int>& nums) {
        int n = nums.size();  // Total number of elements

        for (int i = 1; i < n; i++) {
            int key = nums[i]; // Element to be inserted
            int j = i - 1;

            // Shift elements to right if they are greater than key
            while (j >= 0 && nums[j] > key) {
                nums[j + 1] = nums[j];
                j--;
            }

            nums[j + 1] = key; // Insert the key at correct position
        }

        return nums;
    }
};

int main() {
    Solution solution;

    vector<int> nums = {13, 46, 24, 52, 20, 9};

    cout << "Before Using Insertion Sort: " << endl;
    for (int num : nums)
        cout << num << " ";
    cout << endl;

    nums = solution.insertionSort(nums);

    cout << "After Using Insertion Sort: " << endl;
    for (int num : nums)
        cout << num << " ";
    cout << endl;

    return 0;
}
```

---

### 🧮 **Dry Run Example**

Input: `{13, 46, 24, 52, 20, 9}`

**Pass 1 (i=1)**:
key = 46 → already greater than 13 → no change → `{13, 46, 24, 52, 20, 9}`

**Pass 2 (i=2)**:
key = 24 → shift 46 → insert 24 → `{13, 24, 46, 52, 20, 9}`

**Pass 3 (i=3)**:
key = 52 → already in place → `{13, 24, 46, 52, 20, 9}`

**Pass 4 (i=4)**:
key = 20 → shift 52, 46, 24 → insert 20 → `{13, 20, 24, 46, 52, 9}`

**Pass 5 (i=5)**:
key = 9 → shift all → insert 9 → `{9, 13, 20, 24, 46, 52}`

---

### 📊 Time and Space Complexity

| Case       | Comparisons | Shifts | Time Complexity       |
| ---------- | ----------- | ------ | --------------------- |
| Best Case  | O(n)        | O(1)   | O(n) (already sorted) |
| Average    | O(n²)       | O(n²)  | O(n²)                 |
| Worst Case | O(n²)       | O(n²)  | O(n²) (reverse order) |
| Space      | -           | -      | O(1) (in-place)       |

---

### ✅ **Key Points**

* **Stable**: Maintains order of equal elements.
* **In-place**: No extra space needed.
* Efficient for **small datasets** or **nearly sorted arrays**.
* **Better than Bubble and Selection Sort** in best-case scenarios.

---
