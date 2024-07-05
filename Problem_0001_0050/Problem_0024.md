# 24. Swap Nodes in Pairs

<!-- ## Intution -->

## Solution
* TC: $O(N)$
* SC: $O(1)$
```cpp
class Solution {
    void swapTwo(ListNode* prev, ListNode* n1, ListNode* n2, ListNode* next){
        prev->next = n2;
        n2->next = n1;
        n1->next = next;
    }
public:
    ListNode* swapPairs(ListNode* head) {
        if (!head || !head->next) return head;
        ListNode *dummy = new ListNode(0, head);
        ListNode *prev = dummy;
        ListNode *next = dummy->next->next->next;
        
        while (next){
            // cout << prev->val << "," << next->val << endl;
            swapTwo(prev, prev->next, prev->next->next, next);
            prev = prev->next->next;
            next = (next->next) ? next->next->next : next->next;
        }
        if (prev->next->next){
            swapTwo(prev, prev->next, prev->next->next, next);
        }
        
        return dummy->next;
    }
};
```