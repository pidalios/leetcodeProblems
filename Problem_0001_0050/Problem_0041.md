# 41. First Missing Positive

<!-- ## Intution -->

## Solution
* TC: $O(N)$
* SC: $O(1)$
```cpp
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        if (nums.size() == 1){
            if (nums[0] == 1) return 2;
            else return 1;
        }
        int s = 0;
        for (int i = 0; i < nums.size(); ++i){
            if (nums[i] <= 0){
                swap(nums[i], nums[s]);
                ++s;
            }
        }
        if (s == nums.size()){
            return 1;
        }
        sort(nums.begin()+s, nums.end());
        if (s == nums.size()){
            if (nums[s-1] == 1) return 2;
            else return 1;
        }
        if (nums[s] != 1) return 1;
        for (int i = s; i < nums.size()-1; ++i){
            if (nums[i+1]-nums[i] > 1) return nums[i]+1;
        }
        return nums[nums.size()-1]+1;
    }
};
```