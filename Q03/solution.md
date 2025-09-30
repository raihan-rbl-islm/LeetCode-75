# Q3. Kids With the Greatest Number of Candies (LC 1431)

- **LeetCode Link:** https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/
- **Topic:** Array / String
- **Difficulty:** Easy
- **Language:** C++

## Intuition
First find the maximum candies any kid currently has. Then each kid who can reach at least that maximum after getting `extraCandies` should be marked `true`; otherwise `false`.

## Approach
1. Compute `maximumCandy = max(candies)`.
2. For each `candies[i]`, check if `candies[i] + extraCandies >= maximumCandy`.
3. Push the boolean result into a `vector<bool>` and return it.

## Complexity
- **Time:** O(n), where `n` is the number of kids.
- **Space:** O(n) for the returned `vector<bool)`.

## C++ Code
```cpp
class Solution {
public:
    vector<bool> kidsWithCandies(vector<int>& candies, int extraCandies) {
        int maximumCandy = *max_element(candies.begin(), candies.end());
        int n = (int)candies.size();

        vector<bool> result(n);
        for (int i = 0; i < n; ++i) {
            result[i] = (candies[i] + extraCandies >= maximumCandy);
        }
        return result;
    }
};
