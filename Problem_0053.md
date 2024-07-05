# 53. Maximum Subarray

## Intution
Kadane's Algorithm
## Solution
* TC: $O(N)$
* SC: $O(1)$
```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int curr = 0, maxi = INT_MIN;
        for (int i : nums){
            curr = max(i, curr+i);
            maxi = max(maxi, curr);
        }
        return maxi;
    }
};
```