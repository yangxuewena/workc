#题目
三数之和
## 问题： 
给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。
## 编程实现：
class Solution {
public:

    vector<vector<int>> threeSum(vector<int>& nums)
    {
        vector<vector<int>> res;
        if (nums.size()<3) return res;
        sort(nums.begin(),nums.end());
        for(int i=0;i<nums.size()-2;i++)
        {
            if(nums[i]>0)
            {
                break;
            }
            if(nums[i]==0)
            {
                if((nums[i]+nums[i+1]+nums[i+2])==0)
                {
                    res.push_back(vector<int>{0,0,0});
                    return res;
                }
                else
                    break;
            }
            if(nums[i]==nums[i-1])
            {
                continue;
            }
            int l=i+1;
            int r=nums.size()-1;
            while(l<r)
            {
                if((nums[i]+nums[l]+nums[r])==0)
                {
                    int a=nums[l];
                    int b=nums[r];
                    res.push_back(vector<int>{nums[i],a,b});
                    l++;
                    r--;
                    while(nums[l]==a){l++;}
                    while(nums[r]==b){r--;}                 
                }
                else if((nums[i]+nums[l]+nums[r])>0)
                {
                    r--;
                }
                else
                {
                    l++;
                }
            }
        }
        return res;      
    }
};
##总结
首先将元素排序，然后从最左边开始，如果有三个元素相加为0，那么就把这三个数push进结果res里，然后排除重复元素。如果a+b+c的和大于0，那么从右边缩小范围，如果小于0，从左边缩小范围。