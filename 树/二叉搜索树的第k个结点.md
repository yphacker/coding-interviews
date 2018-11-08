### [	二叉搜索树的第k个结点](https://www.nowcoder.com/practice/ef068f602dde4d28aab2b210e859150a?tpId=13&tqId=11215&tPage=4&rp=4&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)
#### 题目描述
给定一棵二叉搜索树，请找出其中的第k小的结点。例如， （5，3，7，2，4，6，8）    中，按结点数值大小顺序第三小结点的值为4。
```c++
/*
struct TreeNode {
    int val;
    struct TreeNode *left;
    struct TreeNode *right;
    TreeNode(int x) :
            val(x), left(NULL), right(NULL) {
    }
};
*/
class Solution {
public:
    TreeNode* KthNode(TreeNode* pRoot, int k) {
        if (pRoot == NULL || k == 0) {
            return NULL;
        }
        return KthNodeCore(pRoot, k);
    }
    TreeNode* KthNodeCore(TreeNode* pRoot, int &k) {
        TreeNode* target = NULL;
        if (pRoot->left != NULL) {
            target = KthNodeCore(pRoot->left, k);
        }
        if (target == NULL) {
            if (k == 1) {
                target = pRoot;
            }
            --k;
        }
        if (target == NULL && pRoot->right != NULL) {
            target = KthNodeCore(pRoot->right, k);
        }
        return target;
    }
};
```

```python
# coding=utf-8
# author=yphacker

# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    # 返回对应节点TreeNode
    def KthNode(self, pRoot, k):
        # write code here
        if not pRoot or k == 0:
            return None
        ans = self.inorder(pRoot)
        if k > len(ans):
            return None
        return ans[k - 1]

    def inorder(self, root):
        ans = []
        if root.left:
            ans.extend(self.inorder(root.left))
        ans.append(root)
        if root.right:
            ans.extend(self.inorder(root.right))
        return ans
```