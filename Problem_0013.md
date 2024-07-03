# 13. Roman to Integer 

<!-- ## Intution -->

## Solution
* TC: $O(N)$
* SC: constant
  
### C
```c
int decoder(char c){
    switch (c){
        case 'I': return 1;
        case 'V': return 5;
        case 'X': return 10;
        case 'L': return 50;
        case 'C': return 100;
        case 'D': return 500;
        case 'M': return 1000;
        default: return 0;
    }
}

int romanToInt(char* s) {
    int ans = 0;
    for (int i = 0; i < strlen(s); ++i){
        if (decoder(s[i]) < decoder(s[i+1])){
            ans -= decoder(s[i]);
        }else{
            ans += decoder(s[i]);
        }
    }
    return ans;
}
```

### C++
```cpp
class Solution {
    int decoder(char c){
        switch (c){
            case 'I': return 1;
            case 'V': return 5;
            case 'X': return 10;
            case 'L': return 50;
            case 'C': return 100;
            case 'D': return 500;
            case 'M': return 1000;
            default: return 0;
        }
    }
public:
    int romanToInt(string s) {
        int ans = 0;
        for (int i = 0; i < s.size(); ++i){
            if (decoder(s[i]) < decoder(s[i+1])){
                ans -= decoder(s[i]);
            }else{
                ans += decoder(s[i]);
            }
        }
        return ans;
    }
};
```