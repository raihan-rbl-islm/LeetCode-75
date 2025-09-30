# Q2. Greatest Common Divisor of Strings (LC 1071)

- **LeetCode Link:** https://leetcode.com/problems/greatest-common-divisor-of-strings/
- **Topic:** Array / String
- **Difficulty:** Easy
- **Language:** C++

## Intuition
If two strings share a repeating base, then concatenating them in either order should produce the same result. When that holds, the GCD string length must be `gcd(|str1|, |str2|)`, and the base is the prefix of that length.

## Approach
1. Early check: if `(str1 + str2) != (str2 + str1)`, there is no common base, return `""`.
2. Otherwise, the answer is `str1.substr(0, gcd(len1, len2))`.

This avoids manually constructing repeated strings.

## Complexity
- **Time:** O(n + m) to compare the two concatenations and take the substring.
- **Space:** O(1) extra, not counting the return string.

## C++ Code
```cpp
class Solution {
public:
    string gcdOfStrings(string str1, string str2) {
        if (str1 + str2 != str2 + str1) return "";
        return str1.substr(0, __gcd(str1.size(), str2.size()));
    }
};
