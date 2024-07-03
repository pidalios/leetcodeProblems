# 7. Reverse Integer

<!-- ## Intution -->

## Solution
* TC: $O(N)$
* SC: constant
  
### C++
```cpp
class Solution {
public:
    int reverse(int x) {
        if (x >= 0){
            int sum = 0;
            while (x){
                int k = x % 10;
                if (INT_MAX/10 >= sum){
                    sum *= 10;
                    if (INT_MAX - k >= sum){
                        sum += k;
                    }else{
                        // sum = 0;
                        return 0;
                    }
                }else{
                    return 0;
                }
                x /= 10;
            }
            return sum;
        }else{
            // cout << -INT_MAX -1 << endl;
            if (-INT_MAX-1 < x) x = -x;
            else return 0;
            int sum = 0;
            while (x){
                int k = x % 10;
                if (INT_MAX/10 >= sum){
                    sum *= 10;
                    if (INT_MAX - k >= sum){
                        sum += k;
                    }else{
                        sum = 0;
                    }
                }else{
                    sum = 0;
                }
                x /= 10;
            }
            return -sum;   
        }
    }
};
```
### C
```c
int reverse(int x){
    int sum = 0;
    bool overflow = false;
    while (x != 0){
        int k = x % 10;
        x /= 10;
        if (sum > INT_MAX / 10 || (sum < INT_MIN / 10)) {
            overflow = true;
            break;
        }
        sum *= 10;
        sum += k;
    }
    return (overflow) ? 0 : sum;
}
```