#题目
子数组最大平均数I
## 问题：
#### 
给定 n 个整数，找出平均数最大且长度为 k 的连续子数组，并输出该最大平均数。
## 编程实现：
class Solution {
public:

    double findMaxAverage(vector<int>& nums, int k) 
    {
        int sum=0;
        int max=0;
        for(int i=0;i<k;i++)
        {
            sum=sum+nums[i];
        }
        max=sum;
        for(int j=k;j<nums.size();j++)
        {
            sum=sum+nums[j]-nums[j-k];
            if(sum>max)
            {
                max=sum;
            }
        }
        return max*1.0/k;  
        
    }
};
##总结
先求前k个元素的和，设为最大值，再从k开始，每次右边加一个元素，左边减一个元素。每次都跟max比较，如果大于max则更新max的值，否则继续循环，循环结束后返回平均值即可。