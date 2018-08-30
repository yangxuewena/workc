#题目
有序矩阵中第K小的元素
## 问题： 
给定一个 n x n 矩阵，其中每行和每列元素均按升序排序，找到矩阵中第k小的元素。
## 编程实现：
class Solution(object):
    def kthSmallest(self, matrix, k):
        """
        :type matrix: List[List[int]]
        :type k: int
        :rtype: int
        """
        
        res = []
        for i in range(len(matrix)):
            for j in range(len(matrix[0])):
                res.append(matrix[i][j])
        res.sort()
        return res[k-1]
##总结
两层循环，取出矩阵中元素放在列表res中，对res排序返回第K个元素即可。