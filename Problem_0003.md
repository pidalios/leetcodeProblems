# 3. Longest Substring without Repeating Characters

## Solution
* TC: $O(N^2)$
```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int slen = s.size();
        int max_sublen = 0;
        unordered_map<char, bool> map;
        for (int i = 0; i < slen; ++i){
            int sublen = 0;
            for (int j = i; j < slen; ++j){
                if (!map.count(s[j])){
                    map[s[j]] = true;
                    ++sublen;
                }else{
                    break;
                }
            }
            if (max_sublen <= sublen){
                max_sublen = sublen;
            }
            map.clear();
        }
        return max_sublen; 
    }
};
```