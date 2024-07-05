# 16. 3Sum Closest 

<!-- ## Intution -->

## Solution
* TC: $O(N^2)$
* SC: constant
```cpp
class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
        sort(nums.begin(), nums.end());
        bool flag = 0;
        int min_diff = INT_MAX;
        for (int i = 0; i < nums.size()-2; ++i){
            int j = i+1;
            int k = nums.size()-1;
            while (j < k){
                int val = nums[i] + nums[j] + nums[k];
                int diff;
                if (val < target){
                    diff = target - val;
                    ++j;
                }else if (val > target){
                    diff = val - target;
                    --k;
                }else{
                    diff = 0;
                    ++j; --k;
                }
                if (diff < min_diff){
                    min_diff = diff;
                    flag = (val < target) ? 0 : 1;
                }
            }
        }
        return (flag) ? min_diff + target : target - min_diff;
    }
};
```