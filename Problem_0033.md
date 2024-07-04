# 33. Search in Rotated Sorted Array

<!-- ## Intution -->

## Solution
* TC: $O(\log{N})$
* SC: $O(1)$
```cpp
class Solution {
    int findPivot(vector<int>& nums){
        int left = 0, right = nums.size()-1;
        int mid;
        while (left <= right){
            mid = left + (right - left) / 2;
            if (nums[mid] >= nums[0]){
                left = mid + 1;
            }else{
                right = mid - 1;
            }
        }
        return left;
    }
    
public:
    int search(vector<int>& nums, int target) {
        int pivot = findPivot(nums);
        int left, right;
        if (target >= nums[0]){
            left = 0; right = pivot-1;
        }else{
            left = pivot; right = nums.size()-1;
        }
        while (left <= right){
            int mid = left + (right - left) / 2;
            if (nums[mid] < target){
                left = mid + 1;
            }else if (nums[mid] > target){
                right = mid - 1;
            }else{
                return mid;
            }
        }
        return -1;
    }
};
```