# 21. Merge Two Sorted Lists

<!-- ## Intution -->

## Solution
* TC: $O(M+N)$
* SC: constant

```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode *dummy = new ListNode();
        ListNode *curr = dummy;
        while (list1 && list2){
            if (list1->val < list2->val){
                curr->next = list1;
                curr = list1;
                list1 = list1->next;
            }else{
                curr->next = list2;
                curr = list2;
                list2 = list2->next;
            }
        }
        if (list1) curr->next = list1;
        if (list2) curr->next = list2;
        return dummy->next;
    }
};
```