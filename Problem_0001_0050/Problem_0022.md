# 22. Generate Parentheses

<!-- ## Intution -->

## Solution
* TC: $O()$
* SC: $O()$
```cpp
class Solution {
    void helper(int left, int right, int n, string s, vector<string> &res){
        if (left == right && left == n){
            res.push_back(s);
            return;
        }
        if (left < n){
            helper(left+1, right, n, s + '(', res);
        }
        if (right < left){
            helper(left, right+1, n, s + ')', res);
        }
    }
public:
    vector<string> generateParenthesis(int n) {
        vector<string> res;
        helper(0, 0, n, "", res);

        return res;
    }
};
```