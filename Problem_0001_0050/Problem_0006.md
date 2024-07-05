# 6. Zigzag Conversion

<!-- ## Intution -->

## Solution
* TC: $O(N)$
<!-- * SC: $O()$ -->
```c
char* convert(char* s, int numRows) {
    int sLen = strlen(s);
    int group = 2*numRows-2;
    if (group == 0) return s;
    int numCols = (sLen / group + 1) * (numRows-1);
    // printf("sLen = %d, group = %d, numCol = %d\n", sLen, group, numCols);

    // Initialize matrix
    char **matrix = (char**)malloc(sizeof(char*)*numRows);
    for (int i = 0; i < numRows; ++i){
        matrix[i] = (char*)malloc(sizeof(char)*numCols);
        for (int j = 0; j < numCols; ++j){
            matrix[i][j] = '*';
        }
    }


    // Convert
    int u = 0, v = 0;
    int zigFlag = 0;
    for (int i = 0; i < sLen; ++i){
        if (u == numRows-1){
            zigFlag = 1;
        }
        else if (u == 0){
            zigFlag = 0;
        }
        // printf("u, v = %d, %d\n", u, v);
        matrix[u][v] = s[i];

        if (zigFlag == 0){
            u++;
        }
        if (zigFlag == 1){
            u--;
            v++;
        }

    }
    for (int i = 0; i < numRows; ++i){
        for (int j = 0; j < numCols; ++j){
            printf("%c ", matrix[i][j]);
        }
        printf("\n");
    }

    char *out = (char*)malloc(sizeof(char)*(sLen+1));
    out[sLen] = '\0';
    int idx = 0;
    for (int i = 0; i < numRows; ++i){
        for (int j = 0; j < numCols; ++j){
            // printf("%c ", matrix[i][j]);
            if (matrix[i][j] != '*'){
                out[idx] = matrix[i][j];
                ++idx;
            }
        }
    }  
    return out;
}
```