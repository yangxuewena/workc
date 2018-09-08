#题目
颜色分类
## 问题： 
给定一个包含红色、白色和蓝色，一共?n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。
此题中，我们使用整数 0、?1 和 2 分别表示红色、白色和蓝色。
## 编程实现：
class Solution(object):

    def sortColors(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        i = 0
        l = 0
        r = len(nums)-1
        while i <= r:
            if nums[i] == 2:
                nums[i],nums[r] = nums[r],nums[i]
                r = r -1
            elif nums[i] == 0:
                nums[i],nums[l] = nums[l],nums[i]
                l = l + 1
                i = i + 1
            elif nums[i] == 1:
                i = i+1
##总结
设置两个指针分别指向首尾两端，从头开始判断nums中每个元素，若为2，将该元素移到最右端，同时r减一；若为0，将该元素移到最左端，同时l加一；若为1跳过继续。