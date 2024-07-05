# 2058. Find the Minimum and Maximum Number of Nodes Between Critical Points

## Intution
1. First create a vector to record crtitcal points.
2. If size of the vector less than 2, return `{-1, -1}`
3. The maximum difference is `points[n-1] - points[0]` and iterate through the vector to find minimum difference.

## Solution
* TC: $O(N)$
* SC: $O(N)$
```cpp
class Solution {
public:
    vector<int> nodesBetweenCriticalPoints(ListNode* head) {
        if (!head->next->next) return {-1, -1};
        ListNode *curr = head->next;
        ListNode *prev = head;
        ListNode *next = curr->next;
        vector<int> points;
        int idx = 1;
        while (next){
            if (prev->val < curr->val && next->val < curr->val){
                points.push_back(idx);
                ++idx;
            }else if (prev->val > curr->val && next->val > curr->val){
                points.push_back(idx);
                ++idx;
            }else{
                ++idx;
            }
            prev = prev->next;
            curr = curr->next;
            next = next->next;
        }
        if (points.size() < 2) return {-1, -1};
        int maxi = points[points.size()-1] - points[0];
        int mini = INT_MAX;
        for (int i = 0; i < points.size()-1; ++i){  
            int diff = points[i+1] - points[i];
            mini = min(diff, mini);
        }
        return {mini, maxi};
    }
};
```