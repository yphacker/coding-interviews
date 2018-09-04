### [最小的K个数](https://www.nowcoder.com/practice/6a296eb82cf844ca8539b57c23e6e9bf?tpId=13&tqId=11182&tPage=2&rp=2&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)
#### 题目描述
输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4,。
```c++
typedef multiset<int, greater<int> > inSet;
typedef multiset<int, greater<int> >::iterator setInterator;
class Solution {
public:
    vector<int> GetLeastNumbers_Solution(vector<int> input, int k) {
        vector<int> ans;
        inSet leastNumbers;
        if (k < 1 || input.size() < k) {
            return ans;
        }
        setInterator it;
        for (int i = 0; i < input.size(); ++i) {
            if (leastNumbers.size() < k) {
                leastNumbers.insert(input[i]);
            } else {
                setInterator it = leastNumbers.begin();
                if(input[i] < *it) {
                    leastNumbers.erase(it);
                    leastNumbers.insert(input[i]);
                }
            }
        }
        for (it = leastNumbers.begin(); it != leastNumbers.end(); ++it) {
            ans.push_back(*it);
        }
        return ans;
    }
};
```
||基于Partition函数的思路|基于堆或者红黑树的思路|
|时间复杂度|O(n)|O(n*logk)|
|是否需要修改输入数组|是|否|
|是否适用于海量数据|否|是|