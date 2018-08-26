#题目
两数相除
## 问题： 
给定两个整数，被除数 dividend 和除数 divisor。将两数相除，要求不使用乘法、除法和 mod 运算符。
返回被除数 dividend 除以除数 divisor 得到的商。
## 编程实现：
class Solution(object):

    def divide(self, dividend, divisor):
        """
        :type dividend: int
        :type divisor: int
        :rtype: int
        """
        if dividend == 0:
            return 0
        elif (dividend > 0 and divisor > 0) or (dividend < 0 and divisor < 0):
            flag = 1
            dividend = abs(dividend)
            divisor = abs(divisor)
        else:
            flag = -1
            dividend = abs(dividend)
            divisor = abs(divisor)
        result = flag * ( dividend // divisor)
        if -2**(31) <= result <= 2**(31)-1:
            return result
        else:
            return 2**(31)-1
##总结
定义一个变量flag,用来存放结果的符号，对被除数和除数分别取绝对值，计算结果result，与flag相乘，看是否在规定范围内，返回result。