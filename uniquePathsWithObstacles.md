#题目
不同路径2
## 问题： 
一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为“Start” ）。
机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为“Finish”）。
现在考虑网格中有障碍物。那么从左上角到右下角将会有多少条不同的路径？
## 编程实现：
class Solution(object):
    def uniquePathsWithObstacles(self, obstacleGrid):
        """
        :type obstacleGrid: List[List[int]]
        :rtype: int
        """
        m = len(obstacleGrid)
        n = len(obstacleGrid[0])
        if obstacleGrid[0][0] == 1:
            return 0       
        if m == 1 and n == 1 and obstacleGrid[0][0] == 0:
            return 1   
         #处理边界
        for i in range(1,m):
            if obstacleGrid[i][0] == 0:
                obstacleGrid[i][0] = 1
            elif obstacleGrid[i][0] == 1:
                for j in range(i,m):
                    obstacleGrid[j][0] = 0
                break
        for i in range(1,n):
            if obstacleGrid[0][i] == 0:
                obstacleGrid[0][i] = 1
            elif obstacleGrid[0][i] == 1:
                for j in range(i,n):
                    obstacleGrid[0][j] = 0
                break
        #其余位置
        for i in range(1,m):
            for j in range(1,n):
                if obstacleGrid[i][j] == 1:
                    obstacleGrid[i][j] = 0
                else:
                    obstacleGrid[i][j] = obstacleGrid[i][j-1] + obstacleGrid[i-1][j]
        return obstacleGrid[m-1][n-1]
                
        
##总结
使用动态规划，先处理边界，再处理内部。