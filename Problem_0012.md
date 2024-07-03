# 12. Integer to Roman

<!-- ## Intution -->

## Solution
* TC: constant
* SC: constant
```cpp
class Solution {
public:
    string intToRoman(int num) {
        vector<string> tho = {"", "M", "MM", "MMM"};
        vector<string> hun = {"", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"};
        vector<string> ten = {"", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"};
        vector<string> one = {"", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"};
        return tho[num/1000] + hun[(num/100)%10] + ten[(num/10)%10] + one[num%10];
    }
}
```