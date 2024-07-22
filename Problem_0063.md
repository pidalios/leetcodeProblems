# 63. Unique Paths II

## Intution
Dynamic programming approach.

## Solution
* TC: $O(N^2)$
* SC: $O(N^2)$
```cpp
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        int m = obstacleGrid.size();
        int n = obstacleGrid[0].size();
        if (obstacleGrid[0][0] == 1) return 0;

        obstacleGrid[0][0] = 1;
        for (int i = 0; i < m; ++i){
            for (int j = 0; j < n; ++j){
                if (obstacleGrid[i][j]){
                    if (!(i == 0 && j == 0))
                        obstacleGrid[i][j] = 0;
                }
                else if (i > 0 && j > 0){
                    obstacleGrid[i][j] = obstacleGrid[i][j-1] + obstacleGrid[i-1][j];
                }
                else if (i > 0){
                    obstacleGrid[i][0] = obstacleGrid[i-1][0];
                }
                else if (j > 0){
                    obstacleGrid[0][j] = obstacleGrid[0][j-1];
                }
            }
        }
        return obstacleGrid[m-1][n-1];
    }
};
```