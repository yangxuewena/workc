#题目
反转数字
## 问题： 
给定一个 32 位有符号整数，将整数中的数字进行反转。
## 编程实现：
class Solution {
public:

    int reverse(int x) 
    {
        const int int_max=0x7fffffff;
        const int int_min=0x80000000;
        long long ans = 0;
        while(x!=0)
        {
            ans=ans*10+(x%10);
            x=x/10;
        }
        if(ans<int_min || ans>int_max)
        {
              ans=0;
        }
        return ans;
    }
};
##总结
从最低位开始将每位依次取出，最低位变为最高位，最高位变为最低位，然后判断是否超出范围，超出返回0，不超返回ans。