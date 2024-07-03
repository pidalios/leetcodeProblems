# 20. Valid Parentheses


## Linked List Solution
### Intution
Treated a linked list as a stack, the head of list is the top of stack.

### Approach
1. Initialize a list `(NULL)` (empty stack).
2. Iterate through string `s`.
3. If `s[i] == '(' or '[' or '{'` add `s[i]` to the head of linked list (top of the stack).
4. If `s[i] == ')' or ']' or '}'` check the head of list. If list is empty or brackets cannot be closed, return `false`. Else if brackets can be closed, pop the head of the list `list = list->next`.
5. After the iteration, if the list is empty, it is a valid pattern, else return `false`.
### Solution
* TC: $O(N)$
* SC: $O(N)$
```c
char clo(char c){
    switch(c){
        case ')': return '(';
        case ']': return '[';
        case '}': return '{';
        default:  return '0';
    }
}

bool isValid(char* s) {
    // Treated a singly linked list as a stack.
    struct ListNode *list = NULL;
    for (int i = 0; i < strlen(s); ++i){
        if (s[i] == '(' || s[i] == '[' || s[i] == '{'){
            // Add the char to the top of the stack
            struct ListNode *node = (struct ListNode*)malloc(sizeof(struct ListNode));
            node->next = list;
            node->val = s[i];
            list = node;
        }else if (list){
            // If not the same type of closed bracket, return false
            if (list->val != clo(s[i])) return false;
            // Pop the stack
            list = list->next;
        }else{
            return false;
        }
    }
    // If stack is not empty, return false.
    return !list;
}
```

## Stack
### Solution
* TC: $O(N)$
* SC: $O(N)$
```cpp
class Solution {
    char close(char c){
        switch(c){
            case ')': return '(';
            case ']': return '[';
            case '}': return '{';
            default:  return '0';
        }
    }
public:
    bool isValid(string s) {
        stack<char> st;
        for (int i = 0; i < s.size(); ++i){
            if (s[i] == '(' || s[i] == '[' || s[i] == '{'){
                st.push(s[i]);
            }else if (!st.empty()){
                if (st.top() != close(s[i])){
                    return false;
                }else{
                    st.pop();
                }
            }else if (s[i] == ')' || s[i] == ']' || s[i] == '}'){
                return false;
            }
        }
        return st.empty();
    }
};
```