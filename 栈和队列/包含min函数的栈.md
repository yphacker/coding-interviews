### [包含min函数的栈](https://www.nowcoder.com/practice/4c776177d2c04c2494f2555c9fcc1e49?tpId=13&tqId=11173&tPage=1&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)
#### 题目描述
定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。
```c++
class Solution {
public:
    stack<int> dataStack, minStack;
    void push(int value) {
        dataStack.push(value);
        if (minStack.size()==0 || value <= minStack.top()) {
            minStack.push(value);
        } else {
            minStack.push(minStack.top());
        }
    }
    void pop() {
        if (dataStack.size()>0 && minStack.size()>0) {
            dataStack.pop();
            minStack.pop();
        }
    }
    int top() {
        return dataStack.top();
    }
    int min() {
        return minStack.top();
    }
};
```

```python
# coding=utf-8
# author=yphacker

class Solution:
    def __init__(self):
        self.stack = []
        self.min_stack = []

    def push(self, node):
        # write code here
        self.stack.append(node)
        if not self.min_stack or node <= self.min_stack[-1]:
            self.min_stack.append(node)

    def pop(self):
        # write code here
        if self.stack[-1] == self.min_stack[-1]:
            self.min_stack.pop()
        self.stack.pop()

    def top(self):
        # write code here
        return self.stack[-1]

    def min(self):
        # write code here
        return self.min_stack[-1]
```