
## 📘 Left Rotate Array by K Places 

---

### 🧩 Problem Statement

> Given an array of integers `nums` and an integer `k`, rotate the array to the **left** by **k positions**.
> This means that each element moves `k` places to the left, and the first `k` elements move to the end of the array.

---

### 🧠 Example

```cpp
Input:  nums = {1, 2, 3, 4, 5, 6, 7}, k = 3  
Output: nums = {4, 5, 6, 7, 1, 2, 3}
```

---

### 💡 Concept

We use the **Reversal Algorithm** which performs left rotation in **O(n)** time and **O(1)** space:

#### 🔁 Steps:

1. Reverse the **first k elements**.
2. Reverse the **remaining n-k elements**.
3. Reverse the **entire array**.

#### ⏱ Time Complexity:

* **O(n)** (each reverse is O(n), done 3 times)
* **O(1)** extra space

---

### 🧪 Dry Run

#### Input:

```cpp
nums = {1, 2, 3, 4, 5}, k = 2
```

#### Step-by-Step:

1. Reverse first k = 2 → `[2, 1, 3, 4, 5]`
2. Reverse rest (from 2 to end) → `[2, 1, 5, 4, 3]`
3. Reverse entire → `[3, 4, 5, 1, 2] ✅`

---

### 💻 Code (✅ Correct Code)

```cpp
class Solution {
public:
    void reverseArray(vector<int> &nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }

    void rotateArray(vector<int>& nums, int k) {
        int n = nums.size();
        k = k % n;  // handle k >= n

        reverseArray(nums, 0, k - 1);
        reverseArray(nums, k, n - 1);
        reverseArray(nums, 0, n - 1);
    }
};
```

---

### 🧾 Notes on Edge Cases

| Case               | Output / Behavior               |
| ------------------ | ------------------------------- |
| `k == 0`           | No rotation                     |
| `k == n`           | No rotation                     |
| `k > n`            | Treated as `k % n`              |
| `nums.size() == 0` | Nothing to do (safe if handled) |
| `k < 0`            | Not valid unless asked          |

---

### 📚 Q\&A – Interview + Exam Focus

---

#### ❓ Q1: What is the time complexity of this method?

✅ **O(n)** for each reverse, done 3 times → O(n)

---

#### ❓ Q2: What is the space complexity?

✅ **O(1)** → in-place array reversal

---

#### ❓ Q3: Why do we do 3 reversals?

To simulate rotation:

* First reverse the part to go to the back.
* Then the part to come in front.
* Final reverse restores correct relative positions.

---

#### ❓ Q4: Is this better than rotating one-by-one `k` times?

Yes. Rotating one-by-one is **O(nk)** which is slow for large `k`.
Reversal algorithm is much more efficient.

---

#### ❓ Q5: How to handle very large `k`?

Just use:

```cpp
k = k % nums.size();
```

This ensures rotation behaves correctly even for `k > n`.

---

#### ❓ Q6: Is there a built-in STL function for this?

Yes, `std::rotate()` from `<algorithm>`:

```cpp
std::rotate(nums.begin(), nums.begin() + k, nums.end());
```

---

### 🧠 Practice MCQs

---

**Q1. What will be the output after rotating `{10, 20, 30, 40}` left by 2?**

✅ Output: `{30, 40, 10, 20}`

---

**Q2. Time complexity of rotating left by k using reversal algorithm?**

* a) O(k)
* b) O(k log n)
* ✅ c) O(n)
* d) O(nk)

---

**Q3. Which of the following STL functions can do left rotation by k?**

* ✅ `std::rotate(v.begin(), v.begin() + k, v.end());`

---

### ✅ Summary Table

| Feature              | Value              |
| -------------------- | ------------------ |
| Rotation Type        | Left by `k`        |
| Time Complexity      | O(n)               |
| Space Complexity     | O(1)               |
| Algorithm Used       | Reversal Algorithm |
| In-place             | ✅ Yes              |
| STL Alternative      | `std::rotate()`    |
| Interview Importance | ⭐⭐⭐⭐☆ (High)       |

---

