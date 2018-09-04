#题目
第K个排列
## 问题： 
给出集合 [1,2,3,…,n]，其所有元素共有 n! 种排列。
给定 n 和 k，返回第 k 个排列。
## 编程实现：
class Solution(object):

    def getPermutation(self, n, k):
        """
        :type n: int
        :type k: int
        :rtype: str
        """
        self.fac = [1,1,2,6,24,120,720,5040,40320,362880]
        i = n-1
        num = list(range(1,n+1))
        ret = ""
        while i >= 0:
            a,b = k // self.fac[i],k % self.fac[i]
            if b == 0:
                a -= 1
            if a >= 0:
                ret += str(num[a])
                del num[a]
                i -= 1
            k = b
            if b == 0:
                for i in reversed(num):
                    ret += str(i)
                break
        return ret
##总结
从一个[1，n]的区间内挑数字加入答案，需要通过数学判断。比如n=4,证明一共有4!种排序，先确定这个排序的第一个数字。对于每个数字开头的序列，在它确定的情况下，一共有(n-1)!种情况。比如1开头的n=4的序列，一共有3！种情况。就可以通过k//(n-1)!来确定这是以哪个数字开头的序列，如果等于0,那就是1，如果等于1那就是2，以此类推。

 