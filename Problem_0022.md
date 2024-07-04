# 22. Generate Parentheses

<!-- ## Intution -->

## Solution
* TC: $O()$
* SC: $O()$
```cpp
class Solution {
    void dfs(int left, int right, int n, string s, vector<string> &res){
        if (left == right && left == n){
            res.push_back(s);
            return;
        }
        if (left < n){
            dfs(left+1, right, n, s + '(', res);
        }
        if (right < left){
            dfs(left, right+1, n, s + ')', res);
        }
    }
public:
    vector<string> generateParenthesis(int n) {
        vector<string> res;
        dfs(0, 0, n, "", res);

        return res;
    }
};
```