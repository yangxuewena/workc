#题目
在排序数组中查找元素的第一个和最后一个位置
## 问题： 
给定一个按照升序排列的整数数组 nums，和一个目标值 target。找出给定目标值在数组中的开始位置和结束位置。
你的算法时间复杂度必须是 O(log n) 级别。
如果数组中不存在目标值，返回 [-1, -1]。
## 编程实现：
class Solution {
public:

    vector<int> searchRange(vector<int>& nums, int target)
    {
        vector<int> res;
        vector<int> res1;
        for(int i=0;i<nums.size();i++)
        {
            if(nums[i]==target)
            {
                res.push_back(i);
            }
        }
        if(res.size()==0) 
        {
            res.push_back(-1);
            res.push_back(-1);
            return res;
        }
        else if(res.size()==1)
        {
            res.push_back(res[0]);
            return res;
        }
        else
        {
            res1.push_back(res[0]);
            res1.push_back(res[res.size()-1]);
            return res1;
        }
       
    }
};
##总结
遍历一遍数组，元素等于目标值就把位置存起来，然后看存放的位置的个数，若没有存入-1然后返回;若只有一个就把改位置再存一遍然后返回；若大于两个就只返回第一个和最后一个。