# 11. Container With Most Water

<!-- ## Intution -->

## Solution
* TC: $O(N)$
* SC: constant
```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int left = 0;
        int right = height.size()-1;
        int max_area = 0;
        int area;
        while (left < right){
            area = (right - left) * min(height[left], height[right]);
            max_area = max(area, max_area);
            if (height[left] < height[right]) ++left;
            else --right;
        }
        return max_area;
    }
}
```