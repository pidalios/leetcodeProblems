# Minimum Difference Between Largest and Smallest Value in Three Moves

## Solution
* TC: $O(N\log{N})$
* SC: constant
```cpp
class Solution {
public:
    int minDifference(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int n = nums.size();
        if (n <= 3) return 0;
        int d1 = nums[n-1] - nums[3];
        int d2 = nums[n-2] - nums[2];
        int d3 = nums[n-3] - nums[1];
        int d4 = nums[n-4] - nums[0];
        return min({d1, d2, d3, d4});
    }
}
```