# 55. Jump Game

## Intution

## Solution
* TC: $O(N)$
* SC: $O(1)$
```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int idx = 0;
        for (int i = 0; i < nums.size(); ++i){
            if (i <= idx) idx = max(idx, nums[i]+i);
        }
        return idx >= nums.size()-1;
    }
};
```