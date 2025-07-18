# GFG POTD - LCM Triplet (18 July 2025)

## 🧠 Problem Summary

Given a number `n`, the task is to find the **maximum possible LCM of any triplet (a, b, c)** such that:

- `1 ≤ a < b < c ≤ n`

Return the maximum LCM value among all such triplets.

---

## ✅ Approach

Brute-forcing all triplets would be too slow for large `n`. Instead, we rely on **mathematical observations**:

### Key Observations:

1. **LCM of three numbers close to `n` gives the largest value.**
2. **For odd `n`:**  
   - Use the triplet `(n, n-1, n-2)` (no common divisors).
3. **For even `n`:**
   - If `n` is **not divisible by 3**, use `(n, n-1, n-3)`
   - If `n` **is divisible by 3**, use `(n-1, n-2, n-3)` (to avoid common divisors)

These give the **maximum LCM** without checking all combinations.

---

## 💡 Final Formula Logic

```python
if n < 3:
    return n
if n is odd:
    return n * (n - 1) * (n - 2)
if n is even and not divisible by 3:
    return n * (n - 1) * (n - 3)
if n is even and divisible by 3:
    return (n - 1) * (n - 2) * (n - 3)

Time & Space Complexity
Time Complexity: O(1) – Constant time computation
Space Complexity: O(1) – No extra space used

Code (Python 3)

class Solution:
    def lcmTriplets(self, n):
        return n if n < 3 else n * (n - 1) * (n - 2) if n & 1 else \
               n * (n - 1) * (n - 3) if n % 3 else (n - 1) * (n - 2) * (n - 3)


Contributed by: Swayam Sharma
📅 Date: July 18, 2025
