# 15. 3Sum

<!-- ## Intution -->

## Solution
* TC: $O(N^2)$
* SC: $O(N)$
```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        set<vector<int>> s;
        sort(nums.begin(), nums.end());
        for (int i = 0; i < nums.size()-2; ++i){
            int j = i+1, k = nums.size()-1;
            while (j < k){
                int val = nums[i] + nums[j] + nums[k];
                if (val < 0){
                    while (j < nums.size()-1 && nums[j] == nums[j+1]){
                        ++j;
                    }
                    ++j;
                }else if (val > 0){
                    while (k > 0 && nums[k] == nums[k-1]){
                        --k;
                    }
                    --k;
                }else{
                    s.insert({nums[i], nums[j], nums[k]});
                    ++j; --k;
                }
            }
        }
        vector<vector<int>> comb;
        for (auto i : s){
            comb.push_back(i);
        }
        return comb;
    }
};
```