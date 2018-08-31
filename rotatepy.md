#题目
旋转图像
## 问题： 
给定一个 n × n 的二维矩阵表示一个图像。
将图像顺时针旋转 90 度。
## 编程实现：
class Solution(object):

    def rotate(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: void Do not return anything, modify matrix in-place instead.
        """
        length = len(matrix)
        for i in range(length):
                for j in range(i+1,length):
                    temp = matrix[i][j]
                    matrix[i][j] = matrix[j][i]
                    matrix[j][i] = temp
        for i in range(len(matrix)):
            matrix[i] = matrix[i][::-1]
        
##总结
调用两层for循环，先变换最外层，逐渐向内深入。