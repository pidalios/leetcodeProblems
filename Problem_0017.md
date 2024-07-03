# 17. Letter Combinations of a Phone Number

<!-- ## Intution -->

## Solution
* TC: $O(4^N)$
<!-- * SC: $O()$ -->
```cpp
class Solution {
    void backtrack(string combination, string next_digits, string phone_map[], vector<string>& output) {
        if (next_digits.empty()) {
            output.push_back(combination);
        } else {
            string letters = phone_map[next_digits[0] - '2'];
            for (char letter : letters) {
                backtrack(combination + letter, next_digits.substr(1), phone_map, output);
            }
        }
    }
public:
    vector<string> letterCombinations(string digits) {
        if(digits.empty()) return {};
        string map[] = {"abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
        vector<string> out;
        backtrack("", digits, map, out);
        return out;
        
    }
};
```