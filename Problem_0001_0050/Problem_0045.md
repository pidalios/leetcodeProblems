# 45. Jump Game II

<!-- ## Intution -->

## Solution
* TC: $O(N^2)$
* SC: $O(N)$
```cpp
class Solution {
public:
    int jump(vector<int>& nums) {
        if (nums.size() == 1) return 0;
        vector<int> dp(nums.size(), 0);
        for (int i = 0; i < nums.size(); ++i){
            int tmp = dp[i];
            for (int j = i; j <= min<int>(nums.size()-1, i + nums[i]); ++j){
                if (dp[j] == 0) dp[j] = tmp + 1;
            }
        }
        return dp[dp.size()-1];
    }
};
```