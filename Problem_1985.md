# 1985. Find the Kth Largest Integer in the Array

<!-- ## Intution -->

## Solution
* TC: $O(N^2\log{N})$
* SC: $O()$
```cpp
class Solution {
    static bool cmp(string a, string b){
        if (a.size() == b.size()){
            int ptr = 0;
            while (ptr < a.size()){
                if (a[ptr]== b[ptr]){
                    ++ptr;
                }else{
                    return a[ptr] < b[ptr];
                }
            }
        }
        return a.size() < b.size();
    }
public:
    string kthLargestNumber(vector<string>& nums, int k) {
        sort(nums.begin(), nums.end(), cmp);
        return nums[nums.size()-k];
    }
};
```