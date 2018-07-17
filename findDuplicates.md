#题目
数组中重复的数据
## 问题： 
给定一个整数数组 a，其中1 ≤ a[i] ≤ n （n为数组长度）, 其中有些元素出现两次而其他元素出现一次。

找到所有出现两次的元素。
## 编程实现：
C++
class Solution {
public:

    vector<int> findDuplicates(vector<int>& nums) {
         vector<int> ans;
    int s=nums.size();
    for(int i=0;i<s;i++)
    {
        int m = abs(nums[i])-1; 
        if (nums[m]>0)
            nums[m]=-nums[m];
        else
            ans.push_back(m+1);
    }
    return ans;
    }
};
##总结
遍历数组，如果nums[m]为正，就将nums[m]改为相反数，说明m+1出现了一次，如果nums[m]为负，这说明m+1已经出现了一次，这次是第二次出现，所以将数组中第m+1个数放入ans中。