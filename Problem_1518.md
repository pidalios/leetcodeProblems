# 1518. Water Bottles

<!-- ## Intution -->

## Solution
* TC: $O(N)$
* SC: $O(1)$
```cpp
class Solution {
public:
    int numWaterBottles(int numBottles, int numExchange) {
        int drink = numBottles;
        int empty = numBottles;
        int remain = 0;
        while (empty >= numExchange){
            remain = empty % numExchange;
            empty /= numExchange;
            drink += empty;
            empty += remain;
        }
        return drink;
    }
};
```