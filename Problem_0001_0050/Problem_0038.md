# 38. Count and Say

## Intution

## Solution
* TC: $O(N^2)$
* SC: $O(1)$
```cpp
class Solution {
    string rle(string s){
        int i = 0;
        string out = "";
        while (i < s.size()){
            int j = i;
            int count = 0;
            while (j < s.size()){
                if (s[i] == s[j]){
                    ++count;
                    ++j;
                }else{
                    break;
                }
            }
            out += (count + '0');
            out += s[i];
            i = j;
        }
        return out;
    }
public:
    string countAndSay(int n) {
        string prev = "1";
        string ans;
        for (int i = 1; i < n; ++i){
            ans = rle(prev);
            prev = ans;
        }
        return prev;
    }
};
```