# 14. Longest Common Prefix

<!-- ## Intution -->

## Solution
$M$ is size of `strs`,
$N$ is the longest length of string
* TC: $O(M*N)$
* SC: constant
```cpp
class Solution {
    string compair(string w1, string w2){
        int len = min(w1.size(), w2.size());
        string s = "";
        for (int i = 0; i < len; ++i){
            if (w1[i] != w2[i]) break;
            else s += w1[i];
        }
        return s;
    }
public:
    string longestCommonPrefix(vector<string>& strs) {
        string s = strs[0];
        for (int i = 1; i < strs.size(); ++i){
            s = compair(strs[i], s);
        }
        return s;
    }
}
```