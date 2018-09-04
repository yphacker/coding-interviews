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