# 1. Two Sum

## Solution
### Brute force
* TC: $O(N^2)$
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> out;
        for (int i = 0; i < nums.size(); ++i){
            for (int j = i+1; j < nums.size(); ++j){
                if (nums[i] + nums[j] == target){
                    out.push_back(i);
                    out.push_back(j);
                }
            }
        }
        return out;
        
    }
};
```

### Hash table
* TC: $O(N)$
* C++
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> map;
        for (int i = 0; i < nums.size(); ++i){
            int res = target - nums[i];
            if (!map.count(res)){
                map[nums[i]] = i;
            }else{
                return {map[res], i};
            }
        }
        return {};
    }
};
```
* Python
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        table = {}
        for i in range(0, len(nums)):
            diff = target - nums[i]
            if (table.get(diff) == None):
                table[nums[i]] = i
            else:
                return [table[diff], i]
        return []
        
```