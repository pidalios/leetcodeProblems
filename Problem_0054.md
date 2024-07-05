# 54. Spiral Matrix

<!-- ## Intution -->

## Solution
* TC: $O(N^2)$
* SC: $O(N^2)$
```cpp
class Solution {
    void vprint(vector<int> ans){
        for (int i : ans){
            cout << i << " ";
        }
        cout << endl;
    }
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> ans;
        int left = 0, right = matrix[0].size()-1;
        int up = 0, down = matrix.size()-1;
        while (left <= right || up <= down){
            if (up <= down){
                for (int i = left; i <= right; ++i){
                    if (matrix[up][i] != INT_MIN) ans.push_back(matrix[up][i]);
                    else break;
                    matrix[up][i] = INT_MIN;
                }
                ++up;
            }
            if (left <= right){
                for (int i = up; i <= down; ++i){
                    if (matrix[i][right] != INT_MIN) ans.push_back(matrix[i][right]);
                    else break;
                    matrix[i][right] = INT_MIN;
                }
                --right;
            }
            if (up <= down){
                for (int i = right; i >= left; --i){
                    if (matrix[down][i] != INT_MIN) ans.push_back(matrix[down][i]);
                    else break;
                    matrix[down][i] = INT_MIN;
                }
                --down;
            }
            if (left <= right){
                for (int i = down; i >= up; --i){
                    if (matrix[i][left] != INT_MIN) ans.push_back(matrix[i][left]);
                    else break;
                    matrix[i][left] = INT_MIN;
                }
                ++left;
            }
        }
        return ans;
    }
};
```