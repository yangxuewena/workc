#题目
反转整数
## 问题： 
给定一个 32 位有符号整数，将整数中的数字进行反转。
## 编程实现：
class Solution(object):

    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        r = 0
        flag = 1
        if x < 0:
            x = abs(x)
            flag = -1
        while x != 0:
            r = r * 10 + x % 10
            x = x // 10
        r = r * flag
        if  -2147483647 < r < 2147483648:
            return r
        else:
            return 0
##总结
首先判断x的符号，若为负数取绝对值然后将flag设为-1，然后依次取出每一位，最后还要判断结果是否在要求区间内，若不在返回0。