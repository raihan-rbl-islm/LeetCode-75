# Q5. Reverse Vowels of a String (LC 345)

- **LeetCode Link:** https://leetcode.com/problems/reverse-vowels-of-a-string/
- **Topic:** Array / String
- **Difficulty:** Easy
- **Language:** C++

## Intuition
We only need to reverse the vowels (`a, e, i, o, u` in both cases).  
Non-vowels should stay in place. This can be done efficiently using the **two-pointer** technique.

## Approach
1. Keep a set of vowels for quick lookup.
2. Use two pointers:
   - `i` starting at the left,
   - `j` starting at the right.
3. Move `i` forward until it points to a vowel.
4. Move `j` backward until it points to a vowel.
5. Swap the two vowels and continue until `i >= j`.
6. Return the modified string.

## Complexity
- **Time:** O(n), where `n = s.size()`. Each character is checked at most twice.
- **Space:** O(1) extra (ignoring the vowel set).

## C++ Code
```cpp
class Solution {
public:
    set<char> vowel = {'a', 'e', 'i', 'o', 'u'};

    bool notVowel(char c) {
        return !vowel.count(tolower(c));
    }

    string reverseVowels(string s) {
        int i = 0, j = s.size() - 1;
        while (i < j) {
            while (notVowel(s[i]) && i < j) i++;
            while (notVowel(s[j]) && i < j) j--;
            swap(s[i], s[j]);
            i++, j--;
        }
        return s;
    }
};
