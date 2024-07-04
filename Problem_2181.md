# 2181. Merge Nodes in Between Zeros

<!-- ## Intution -->

## Solution
* TC: $O(N)$
* SC: $O(1)$
```cpp
class Solution {
public:
    ListNode* mergeNodes(ListNode* head) {
        ListNode *curr = head;
        ListNode *next = curr->next;
        ListNode *prev;
        while (next){
            if (next->val != 0){
                curr->val += next->val;
                next = next->next;
            }else{
                prev = curr;
                curr->next = next;
                curr = curr->next;
                next = curr->next;
            }
        }   
        prev->next = nullptr;
        return head;     
    }
};
```