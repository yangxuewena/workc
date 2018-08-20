#题目
两数之和
## 问题： 
给定一个整数数组和一个目标值，找出数组中和为目标值的两个数。
你可以假设每个输入只对应一种答案，且同样的元素不能被重复利用。
## 编程实现：
class Solution(object):

    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        for i in range(len(nums)):
            for j in range(i+1,len(nums)):
                       if nums[i]+nums[j]==target:
                            return [i,j]
        
##总结
调用两重循环，寻找两个符合条件的下标值。