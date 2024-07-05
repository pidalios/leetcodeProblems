# 59. Spiral Matrix II

<!-- ## Intution -->

## Solution
* TC: $O(N^2)$
* SC: $O(N^2)$
```cpp
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        vector<vector<int>> m(n, vector<int>(n, 0));
        int left = 0, right = n-1;
        int up = 0, down = n-1;
        int num = 0;
        while (left <= right && up <= down){
            for (int i = left; i <= right; ++i){
                m[up][i] = ++num;
            }
            ++up;
            for (int i = up; i <= down; ++i){
                m[i][right] = ++num;
            }
            --right;
            for (int i = right; i >= left; --i){
                m[down][i] = ++num;
            }
            --down;
            for (int i = down; i >= up; --i){
                m[i][left] = ++num;
            }
            ++left;
        }
        return m;
    }
};
```