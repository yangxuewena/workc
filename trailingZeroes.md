#题目
阶乘后的零
## 问题： 
给定一个整数 n，返回 n! 结果尾数中零的数量。
## 编程实现：
class Solution {
public:

    int trailingZeroes(int n) 
    {
        int ret = 0;
        while(n)
        {
            ret += n/5;
            n /= 5;
        }
        return ret;
        
    }
};
##总结
当且仅当因子中出现一对2和5时，结果会增加一个零，2的个数多余5的个数，计算5的个数即可。