# Q4. Can Place Flowers (LC 605)

- **LeetCode Link:** https://leetcode.com/problems/can-place-flowers/
- **Topic:** Array / String
- **Difficulty:** Easy
- **Language:** C++

## Intuition
A flower can be planted at index `i` if the current spot is empty and both neighbors are empty or out of bounds. When we plant at `i`, the next spot `i+1` cannot be used, so we skip it.

## Approach
1. Scan the array once.
2. At each `i`, check:
   - `flowerbed[i] == 0`
   - `i == 0 || flowerbed[i-1] == 0`
   - `i == size-1 || flowerbed[i+1] == 0`
3. If all true, increment `result` and skip the next index.
4. Return whether `result >= n`.

## Complexity
- **Time:** O(m), where `m = flowerbed.size()`.
- **Space:** O(1).

## C++ Code
```cpp
class Solution {
public:
    bool canPlaceFlowers(vector<int>& flowerbed, int n) {
        int result = 0;
        int size = flowerbed.size();
        for (int i = 0; i < size; i ++) {
            int prev = result;
            result += ((flowerbed[i] == 0) && (i == 0 || flowerbed[i - 1] == 0) && (i == size - 1 || flowerbed[i + 1] == 0));
            if (result != prev) i ++;
        }
        return n <= result;
    }
};
