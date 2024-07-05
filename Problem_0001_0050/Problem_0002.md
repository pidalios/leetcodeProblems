# 2. Add Two Numbers
## Solution
* TC: $O(\max(M,N))$
```cpp
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        int carry = 0;
        ListNode *head = l1;
        ListNode *prev = nullptr;
        // while ()
        while (l1 && l2){
            l1->val += l2->val + carry;
            if (l1->val >= 10){
                l1->val -= 10;
                carry = 1;
            }else{
                carry = 0;
            }
            prev = l1;
            l1 = l1->next;
            l2 = l2->next;
        }
        if (l2){
            prev->next = l2;
            l1 = l2;
        }
        while (l1){
            l1->val += carry;
            if (l1->val >= 10){
                l1->val -= 10;
                carry = 1;
            }else{
                carry = 0;
            }
            prev = l1;
            l1 = l1->next;
        }
        if (carry == 1){
            prev->next = new ListNode(carry);
        }
        return head;
    }
};
```