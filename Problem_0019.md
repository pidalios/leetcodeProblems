# 19. Remove Nth Node From End of List

<!-- ## Intution -->

## Solution
* TC: $O(N)$
* SC: constant
```cpp
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        if (!head) return head;
        ListNode *dummy = new ListNode(0, head);
        ListNode *fast = head;
        ListNode *curr = head;
        ListNode *prev = dummy;
        for (int i = 0; i < n; ++i){
            fast = fast->next;
        }
        while (fast){
            prev = curr;
            curr = curr->next;
            fast = fast->next;
        }
        prev->next = curr->next;
        delete curr;
        return dummy->next;
    }
};
```