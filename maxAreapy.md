#题目
盛最多水的容器
## 问题： 
给定 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。
## 编程实现：
class Solution(object):

    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        #逼近法
        max_v = 0
        l = 0
        r = len(height)-1
        while l < r:
            max_v = max(max_v,min(height[l],height[r])*(r-l))
            if height[l]>height[r]:
                r = r - 1
            else:
                l = l + 1
        return max_v
##总结
定义两个指针，分别指向两端，比较出小的一端向中间逼近，每次计算出此时体积，最后返回最大的。