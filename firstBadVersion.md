#题目
第一个错误的版本
## 问题： 
你是产品经理，目前正在带领一个团队开发新的产品。不幸的是，你的产品的最新版本没有通过质量检测。由于每个版本都是基于之前的版本开发的，所以错误的版本之后的所有版本都是错的。
假设你有 n 个版本 [1, 2, ..., n]，你想找出导致之后所有版本出错的第一个错误的版本。
你可以通过调用 bool isBadVersion(version) 接口来判断版本号 version 是否在单元测试中出错。实现一个函数来查找第一个错误的版本。你应该尽量减少对调用 API 的次数。
## 编程实现：
// Forward declaration of isBadVersion API.
bool isBadVersion(int version);

class Solution {
public:

    int firstBadVersion(int n) 
    {
        int l=1;
        int r=n;
        while(l<=r)
        {
            int m=l+(r-l)/2;
            if(isBadVersion(m))
            {
                r=m-1;
            }
            else
            {
                l=m+1;
            }
        }
        return l;
    }
};
##总结
使用二分法，首先记录左端点与右端点，然后判断中点是否是错误的版本，若是，则将中点的前一位赋值给r;若不是，则将中点的后一位赋值给l，再找此时的中点判断。