### [和为S的两个数字](https://www.nowcoder.com/practice/390da4f7a00f44bea7c2f3d19491311b?tpId=13&tqId=11195&tPage=3&rp=3&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)
#### 题目描述
输入一个递增排序的数组和一个数字S，在数组中查找两个数，使得他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。
#### 输出描述
对应每个测试案例，输出两个数，小的先输出。
```c++
class Solution {
public:
    vector<int> FindNumbersWithSum(vector<int> a,int sum) {
        vector<int> ans;
        int l = 0, r = a.size()-1;
        while(l < r){
            if(a[l]+a[r] == sum){
                ans.push_back(a[l]);
                ans.push_back(a[r]);
                break;
            }
            while(l<r && a[l]+a[r]>sum) --r;
            while(l<r && a[l]+a[r]<sum) ++l;
        }
        return ans;
    }
};
```