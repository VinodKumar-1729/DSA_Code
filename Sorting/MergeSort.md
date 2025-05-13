
---

## 🔷 Merge Sort – Notes

### 🔍 **Concept**

**Merge Sort** is a **Divide and Conquer** sorting algorithm that:

1. **Divides** the array into two halves,
2. **Recursively sorts** both halves, and
3. **Merges** the sorted halves into a single sorted array.

---

### ⚙️ **How Merge Sort Works**

1. Recursively split the array until each part has one element.
2. Merge two sorted parts into one sorted array.
3. Repeat merging until the full array is sorted.

---

### 🧠 **Algorithm Steps**

```cpp
mergeSort(arr[], low, high)
    if low >= high
        return
    mid = (low + high) / 2
    mergeSort(arr, low, mid)
    mergeSort(arr, mid + 1, high)
    merge(arr, low, mid, high)
```

---

### 📊 **Time and Space Complexity**

| Case         | Time Complexity | Space Complexity |
| ------------ | --------------- | ---------------- |
| Best Case    | O(n log n)      | O(n)             |
| Average Case | O(n log n)      | O(n)             |
| Worst Case   | O(n log n)      | O(n)             |

* **Stable**: Yes
* **In-place**: No (uses temporary array)
* Best suited for **linked lists** and **large datasets**.

---

### 🧪 **Dry Run Example**

Input: `{9, 4, 7, 6, 3, 1, 5}`

* **Divide** into: `{9, 4, 7, 6}` and `{3, 1, 5}`
* Further split: `{9, 4}`, `{7, 6}`, `{3}`, `{1, 5}`
* Recursively merge:

  * `{9, 4}` → `{4, 9}`
  * `{7, 6}` → `{6, 7}`
  * `{1, 5}` → `{1, 5}`
* Merge step-by-step:

  * `{4, 9}` + `{6, 7}` → `{4, 6, 7, 9}`
  * `{1, 5}` + `{3}` → `{1, 3, 5}`
* Final merge: `{4, 6, 7, 9}` + `{1, 3, 5}` → `{1, 3, 4, 5, 6, 7, 9}`

---

## 🧾 Final C++ Code Summary

```cpp
#include <bits/stdc++.h>
using namespace std;

class Solution{
public:
    // Function to merge two sorted halves of the array
    void merge(vector<int> &arr, int low, int mid, int high) {
        // Temporary array to store merged elements
        vector<int> temp;
        int left = low;
        int right = mid + 1;

        // Loop until subarrays are exhausted
        while (left <= mid && right <= high) {
            // Compare left and right elements
            if (arr[left] <= arr[right]) {
                // Add left element to temp
                temp.push_back(arr[left]);
                // Move left pointer
                left++;
            }
            else {
                // Add right element to temp
                temp.push_back(arr[right]);
                // Move right pointer
                right++;
            }
        }

        // Adding the remaining elements of left half
        while (left <= mid) {
            temp.push_back(arr[left]);
            left++;
        }

        // Adding the remaining elements of right half
        while (right <= high) {
            temp.push_back(arr[right]);
            right++;
        }

        // Transferring the sorted elements to arr
        for (int i = low; i <= high; i++) {
            arr[i] = temp[i - low];
        }
    }
    
    // Helper function to perform merge sort from low to high
    void mergeSortHelper(vector<int> &arr, int low, int high){
        // Base case: if the array has only one element
        if (low >= high)
            return;
        
        // Find the middle index
        int mid = (low + high) / 2;
        // Recursively sort the left half
        mergeSortHelper(arr, low, mid);
        // Recursively sort the right half
        mergeSortHelper(arr, mid + 1, high);
        // Merge the sorted halves
        merge(arr, low, mid, high);
    }
    
    // Function to perform merge sort on the given array
    vector<int> mergeSort(vector<int> &nums) {
        int n = nums.size(); // SIze of array
        
        // Perform Merge sort on the whole array
        mergeSortHelper(nums, 0, n-1);
        
        // Return the sorted array
        return nums;
    }
};

int main(){
    vector<int> arr = {9, 4, 7, 6, 3, 1, 5};
    int n = arr.size();

    cout << "Before Sorting Array: " << endl;
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;

    // Create an instance of the Solution class
    Solution sol;
    // Function call to sort the array
    vector<int> sortedArr = sol.mergeSort(arr);

    cout << "After Sorting Array: " << endl;
    for (int i = 0; i < n; i++)
        cout << sortedArr[i] << " ";
    cout << endl;

    return 0;
}
```

---

## ✅ Key Advantages of Merge Sort

* Guarantees O(n log n) time
* Good for **large** datasets
* Preferred for **linked lists**
* Can be modified for **external sorting** (e.g., sorting large files)

---
