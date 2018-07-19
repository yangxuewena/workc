#题目
最长连续递增序列
## 问题：
#### 
给定一个未经排序的整数数组，找到最长且连续的的递增序列。
## 编程实现：
class Solution {
public:

    int findLengthOfLCIS(vector<int>& nums) 
    {
         int n =nums.size();
         if(n <= 1)return n;
         int ret = 1,length=1;
         for(int i=1;i<n;i++)
         {
            if(nums[i]>nums[i-1])length++;
            else length =1;
            ret = max(length,ret);
        }
        return ret;
    }
};

## 总结体会：
思路：若数组长度小于等于1，返回字符串的长度；若大于1，则开始遍历数组，若nums[i]>nums[i-1]，长度加1，并与之前记录的最大长度比较取最大的，若不满足nums[i]>nums[i-1]，则重新开始记录长度。