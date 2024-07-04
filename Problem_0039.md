# 39. Combination Sum

<!-- ## Intution -->

## Solution
<!-- * TC: $O()$
* SC: $O()$ -->
```cpp
class Solution {
    void combination(vector<int> &candidates, int target, vector<int> &comb, int sum, int idx, vector<vector<int>> &out){
        if (sum > target) return;
        if (sum == target){
            out.push_back(comb);
            return;
        }
        for (int i = idx; i < candidates.size(); ++i){
            comb.push_back(candidates[i]);
            sum += candidates[i];
            combination(candidates, target, comb, sum, i, out);
            comb.pop_back();
            sum -= candidates[i];
        }
    }
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<vector<int>> out;
        vector<int> comb;
        combination(candidates, target, comb, 0, 0, out);
        return out;
        
    }
};
```