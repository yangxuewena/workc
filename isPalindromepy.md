#题目
回文数
## 问题： 
判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。
## 编程实现：
class Solution(object):

    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        if x < 0:
            return False
        elif str(x)==str(x)[::-1]:
            return True
        else:
            return False
##总结
如果该数小于0，不是回文数，返回FALSE，如果该数大于0，将其转化为字符串形式，判断该字符串是否和起反转后的字符串相等，若相等原数为回文数，不相等原数不是回文数。