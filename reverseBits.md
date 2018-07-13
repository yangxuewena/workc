#题目
颠倒二进制位
## 问题： 
颠倒给定的 32 位无符号整数的二进制位。
## 编程实现：
class Solution {
public:

    uint32_t reverseBits(uint32_t n) 
    {
         uint32_t sum = 0;
        int count = 0;
        while(n)
        {
            sum = sum * 2 + n%2;
            n = n>>1;
            ++count;
        }
        for(int i = count; i < 32; ++i)
            sum = sum *2;
        return sum;

    }
};
##总结
将n不断右移一位，每次取出最后一位，将上一次的结果乘以2加上下一次的结果，若不足32位，不断乘2，用0补齐最低位。