# 28. Find the Index of the First Occurrence in a String

<!-- ## Intution -->

## Solution

### KMP Algorithm
* TC: $O(N)$
* SC: $O(1)$
```c
// Using KMP algorithm
void nextGen(char *patt, int *next){
    size_t patt_len = strlen(patt);
    int prefix_len = 0;
    int i = 1, j = 1;
    next[0] = 0;
    while (i < patt_len){
        if (patt[prefix_len] == patt[i]){
            i++; prefix_len++;
            next[j] = prefix_len;
            j++;
        }
        else{
            if (prefix_len == 0){
                next[j] = 0;
                i++; j++;
            }
            if (prefix_len > 0){
                prefix_len = next[prefix_len-1];
            }
        }
    }
}
int strStr(char* haystack, char* needle) {
    size_t stack_len = strlen(haystack);
    size_t needle_len = strlen(needle);
    int *next = (int*)malloc(sizeof(int)*needle_len);
    
    nextGen(needle, next);
    int i = 0, j = 0;
    while (i < stack_len){
        if (haystack[i] == needle[j]){
            i++; j++;
        }
        else if (j > 0){
            j = next[j-1];
        }
        else{
            i++;
        }

        if (j == needle_len){
            return i - j;
        }
    }
    return -1;
}
```