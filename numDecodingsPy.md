#题目
编码方法
## 问题： 
给定一个只包含数字的非空字符串，请计算解码方法的总数。
## 编程实现：
class Solution(object):

    def numDecodings(self, s):
        """
        :type s: str
        :rtype: int
        """
       
        l = len(s)
        dp = [1] * l
        #看第一位
        if s[0] == '0':
            return 0
        
        #检测前两位
        temp = int(s[0:2])
        if temp == 10 or temp == 20:
            dp[1] = 1
        elif temp >= 11 and temp <= 26:
            dp[1] = 2
        elif temp > 26:
            if s[1] == '0':
                return 0
            else:
                dp[1] = 1
           
        for i in range(2,l):
            if s[i] == '0':
                if s[i-1] == '1' or s[i-1] == '2':
                    dp[i] = dp[i-2]
                else:
                    return 0
            else:
                if ('1' <= s[i] <= '6' and s[i-1] == '2') or s[i-1] == '1':
                    dp[i] = dp[i-1] + dp[i-2]
                else:
                    dp[i] = dp[i-1]
        return dp[l-1]
        
##总结
用列表dp保存以第i个数字结尾的非空字符串的编码方法的总数，先求出列表中只有一个或两个数字时的情况，从第三个数若满足'1' <= s[i] <= '6' and s[i-1] == '2') or s[i-1] == '1'，利用函数dp[i] = dp[i-1] + dp[i-2]求解，若不满足说明第i个数不可以和前一个数结合，此时的编码方法数为dp[i] = dp[i-1]。遍历结束返回最后一个数。