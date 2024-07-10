# 2582. Pass the Pillow

<!-- ## Intution -->

## Solution
* TC: $O(N)$
* SC: $O(1)$
```cpp
class Solution {
public:
    int passThePillow(int n, int time) {
        int idx = 1;
        int dir = 0;
        while (time){
            --time;
            if (dir == 0){
                ++idx;
                if (idx == n){
                    dir = 1;
                }
            }else{
                --idx;
                if (idx == 1){
                    dir = 0;
                }
            }
        }
        return idx;
    }
};
```