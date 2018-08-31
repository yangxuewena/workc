#题目
字符串转整数
## 问题： 
实现 atoi，将字符串转为整数。
在找到第一个非空字符之前，需要移除掉字符串中的空格字符。如果第一个非空字符是正号或负号，选取该符号，并将其与后面尽可能多的连续的数字组合起来，这部分字符即为整数的值。如果第一个非空字符是数字，则直接将其与之后连续的数字字符组合起来，形成整数。
字符串可以在形成整数的字符后面包括多余的字符，这些字符可以被忽略，它们对于函数没有影响。
当字符串中的第一个非空字符序列不是个有效的整数；或字符串为空；或字符串仅包含空白字符时，则不进行转换。
若函数不能执行有效的转换，返回 0。
## 编程实现：
class Solution(object):

    def myAtoi(self, str):
        """
        :type str: str
        :rtype: int
        """
        s = str.strip()
        syb = 1
        ptr = 0
        res = 0
        if len(s) == 0:
            return 0
        if s[0] == '-':
            syb = -1
            s = s[1:]
        elif s[0] == '+':
            s = s[1:]
        if len(s) == 0:
            return 0
        while s[ptr].isnumeric():
            res = res * 10 + int(s[ptr])
            ptr += 1
            if ptr >= len(s):
                break
        res = res * syb
        if res > 2147483647:
            res =  2147483647
        elif res < -2147483648:
            res = -2147483648
        return res
##总结
先删除字符串前后空格，判断第一个字符是否是'-',将字符串中每个字符取出，最后判断结果是否符合要求，输出。