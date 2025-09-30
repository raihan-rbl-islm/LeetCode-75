# Q1. Merge Strings Alternately (LC 1768)

- **LeetCode Link:** https://leetcode.com/problems/merge-strings-alternately/
- **Topic:** Array / String
- **Difficulty:** Easy
- **Language:** C++

## Intuition
Walk both strings from left to right and take one character from each in turn. When one string finishes, append the remainder of the other string.

## Approach
1. Let `n = min(|word1|, |word2|)`. Interleave the first `n` characters from both strings into the result.
2. Append any leftover characters from the longer string.
3. Return the merged string.

This uses simple indexing and linear time.

## Complexity
- **Time:** O(n + m), where `n = |word1|`, `m = |word2|`.
- **Space:** O(n + m) for the output string. Extra auxiliary space is O(1).

## C++ Code
```cpp
class Solution {
public:
    string mergeAlternately(string word1, string word2) {
        string ss = "";
        int n = min(word1.size(), word2.size());
        for (int i = 0; i < n; i ++) {
            ss += word1[i];
            ss += word2[i];
        }
        while (n < word1.size()) ss += word1[n ++];
        while (n < word2.size()) ss += word2[n ++];
        return ss;
    }
};
