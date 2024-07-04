# 23. Merge k Sorted Lists

<!-- ## Intution -->

## Solution

### Divided and Conquer
* TC: $O(N*\log{K})$
* SC: $O(1)$
```cpp
class Solution {
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode *head = new ListNode(); 
        ListNode *curr = head;
        while (list1 && list2){
            if (list1->val < list2->val){
                curr->next = list1;
                curr = curr->next;
                list1 = list1->next;
            }else{
                curr->next = list2;
                curr = curr->next;
                list2 = list2->next;
            }
        }
        if (list1) curr->next = list1;
        if (list2) curr->next = list2;
        return head->next;
    }
    ListNode* helper(vector<ListNode*>& lists, int left, int right){
        if (left == right) return lists[left];
        if (left + 1 == right) return mergeTwoLists(lists[left], lists[right]);
        int mid = left + (right - left) / 2;
        ListNode *l = helper(lists, left, mid);
        ListNode *r = helper(lists, mid+1, right);
        return mergeTwoLists(l, r);
    }
public:
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        if (lists.size() == 0) return nullptr;
        return helper(lists, 0, lists.size()-1);
    }
};
```