# 50. Pow(x, n)

<!-- ## Intution -->

## Solution
<!-- * TC: $O()$
* SC: $O()$ -->
```cpp
class Solution {
public:
    double myPow(double x, long n) {
        if (n == 0) return 1;
        else if (n < 0){
            return 1 / myPow(x, -n);
        }else{
            return (n%2 == 0) ? myPow(x*x, n/2) : x*myPow(x*x, n/2);
        }
    }
};
```