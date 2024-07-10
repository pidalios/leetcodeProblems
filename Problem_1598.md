# 1598. Crawler Log Folder

<!-- ## Intution -->

## Solution
* TC: $O(N)$
* SC: $O(1)$
```cpp
class Solution {
public:
    int minOperations(vector<string>& logs) {
        int depth = 0;
        for (string s : logs){
            if (s == "../"){
                if (depth > 0){
                    --depth;
                }
            }else if (s == "./"){
                continue;
            }else{
                ++depth;
            }
        }
        return depth;
    }
};
```