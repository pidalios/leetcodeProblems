# 29. Divide Two Integers

<!-- ## Intution -->

## Solution
* TC: $O(N)$
* SC: $O(1)$
```cpp
class Solution {
public:
    int divide(int &dividend, int &divisor) {
        int sign = (dividend < 0) ^ (divisor < 0) ? -1 : 1;

        unsigned int n = abs(dividend);
        unsigned int k = abs(divisor);

        if (k == 1){
            if (dividend == INT_MIN && sign == 1) return INT_MAX;
            if (dividend == INT_MIN && sign == -1) return INT_MIN;
            return sign * n;
        }
        unsigned int q = 0;
        while (n >= k){
            n -= k;
            ++q;
        }
        if ((int) q < 0 && sign == 1) q = INT_MAX;
        return sign * q;
    }
};
```