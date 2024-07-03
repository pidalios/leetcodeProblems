# 18. 4Sum

<!-- ## Intution -->

## Solution
* TC: $O(N^3)$
* SC: constant
```cpp
class Solution {
public:
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        vector<vector<int>> ans;
        if (nums.size() < 4) return ans;
        sort(nums.begin(), nums.end());
        set<vector<int>> s;
        for (int i = 0; i < nums.size()-3; ++i){
            for (int j = i+1; j < nums.size()-2; ++j){
                int u = j+1;
                int v = nums.size()-1;
                while (u < v){
                    int val = nums[i];
                    if (nums[j] > 0){
                        if (INT_MAX - nums[j] >= val) val += nums[j];
                    }else{
                        if (INT_MIN - nums[j] <= val) val += nums[j];
                    }
                    if (nums[u] > 0){
                        if (INT_MAX - nums[u] >= val) val += nums[u];
                    }else{
                        if (INT_MIN - nums[u] <= val )val += nums[u];
                    }
                    if (nums[v] > 0){
                        if (INT_MAX - nums[v] >= val) val += nums[v];
                    }else{
                        if (INT_MIN - nums[v] <= val) val += nums[v];
                    }

                    if (val < target){
                        ++u;
                    }else if (val > target){
                        --v;
                    }else{
                        s.insert({nums[i], nums[j], nums[u], nums[v]});
                        ++u; --v;
                    }
                } 
            }
        }
        for (auto i : s){
            ans.push_back(i);
        }
        return ans;
    }
};
```