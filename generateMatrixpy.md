#题目
螺旋矩阵II
## 问题： 
给定一个正整数 n，生成一个包含 1 到 n2 所有元素，且元素按顺时针顺序螺旋排列的正方形矩阵。
## 编程实现：
class Solution(object):

    def generateMatrix(self, n):
        """
        :type n: int
        :rtype: List[List[int]]
        """
        ans = [[0]*n for i in range(n)]
        t = 1
        direct = 0
        up = 0
        left = 0
        right = n-1
        down = n-1
        while left <= right and up <= down:
            if direct == 0:
                for i in range(left,right+1):
                    ans[up][i] = t
                    t = t +1
                up = up +1
            elif direct == 1:
                for i in range(up,down+1):
                    ans[i][right] = t
                    t = t +1
                right = right -1
            elif direct == 2:
                for i in range(left,right + 1)[::-1]:
                    ans[down][i] = t
                    t = t +1
                down = down -1
            else:
                for i in range(up,down + 1)[::-1]:
                    ans[i][left] = t
                    t = t +1
                left = left +1
            direct = (direct + 1) % 4
        return ans
##总结
程序逻辑分为四个状态，0为向右，1为向下，2为向左，3为向上，还需要四个指针，up 表示上行位置，down表示下行位置，left表示左列位置，right表示右列位置，使用状态转移,由外圈向内圈填充t。