# 58. Length of Last Word

<!-- ## Intution -->

## Solution
* TC: $O(N)$
* SC: $O(1)$
```cpp
class Solution {
public:
    int lengthOfLastWord(string s) {
        int state = 0;
        int count = 0;
        for (int i = s.size()-1; i >= 0; --i){
            if (s[i] != ' '){
                state = 1;
                ++count;
            }else if (state == 1 && s[i] == ' '){
                break;
            }
        }
        return count;
    }
};
```