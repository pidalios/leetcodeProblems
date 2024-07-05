# 34. Find First and Last Position of Element in Sorted Array

<!-- ## Intution -->

## Solution
* TC: $O(\log{N})$
* SC: $O(1)$
```cpp
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        int mid = search_mid(nums, target);
        if (mid < 0) return {-1, -1};
        
        int left = search_left(nums, target, mid);
        int right = search_right(nums, target, mid);
        return {left, right};
    }
private:
    int search_mid(vector<int> &nums, int target){
        int left = 0, right = nums.size()-1;
        while (left <= right){
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) return mid;
            else if (nums[mid] > target) right = mid - 1;
            else left = mid + 1;
        }
        return -1;
    }
    int search_left(vector<int> &nums, int target, int mid){
        int left = 0, right = mid-1;
        while (left <= right){
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) right = mid - 1;
            else left = mid + 1;
        }
        return left;
    }
    int search_right(vector<int> &nums, int target, int mid){
        int left = mid, right = nums.size()-1;
        while (left <= right){
            int mid = left + (right - left) / 2;
            if (nums[mid] != target) right = mid - 1;
            else left = mid + 1;
        }
        return right;
    }

};
```