### [链表中倒数第k个结点](https://www.nowcoder.com/practice/529d3ae5a407492994ad2a246518148a?tpId=13&tqId=11167&tPage=1&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)
#### 题目描述
输入一个链表，输出该链表中倒数第k个结点。
```c++
/*
struct ListNode {
	int val;
	struct ListNode *next;
	ListNode(int x) :
			val(x), next(NULL) {
	}
};*/
class Solution {
public:
    ListNode* FindKthToTail(ListNode* pListHead, unsigned int k) {
        if(pListHead == NULL || k == 0)
            return NULL;
        
    	ListNode *pAhead = pListHead;
        ListNode *pBehind =pListHead;

        for(unsigned int i = 0; i < k-1; ++i){
            if(pAhead->next != NULL) {
                pAhead = pAhead->next;
            }
            else {
                return NULL;
            }
        }
        while(pAhead->next != NULL){
            pAhead = pAhead->next;
            pBehind = pBehind->next;
        }
        return pBehind;
    }
};
```

```python
# coding=utf-8
# author=yphacker

# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def FindKthToTail(self, head, k):
        # write code here
        ans = []
        while head:
            ans.append(head)
            head = head.next
        if k > len(ans) or k < 1:
            return
        return ans[-k]
```