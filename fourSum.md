#题目
四数之和
## 问题： 
给定一个包含 n 个整数的数组 nums 和一个目标值 target，判断 nums 中是否存在四个元素 a，b，c 和 d ，使得 a + b + c + d 的值与 target 相等？找出所有满足条件且不重复的四元组。
## 编程实现：
class Solution {
public:

    vector<vector<int>> fourSum(vector<int>& nums)
    {
        vector<vector<int>> vec;
        vector<int> v(4);
        if(nums.size()<4) return vec;
        sort(nums.begin(),nums.end());
        for(int i=0;i<nums.size()-3;++i){
            for(int j=i+1;j<nums.size()-2;++j){
                int m=target-nums[i]-nums[j];
                int l=j+1,r=nums.size()-1;
                while(l<r){
                    int sum=nums[l]+nums[r];
                    if(m==sum){
                        v[0]=nums[i];
                        v[1]=nums[j];
                        v[2]=nums[l];
                        v[3]=nums[r];
                        vec.push_back(v);
                        ++l;
                        --r;
                        while(l<r&&nums[r]==nums[r+1]) --r;
                        while(l<r&&nums[l]==nums[l-1]) ++l;
        }
                    else if(m<sum){
                        --r;
                    }
                    else{
                        ++l;
                    }
                }
                while(j<nums.size()-2&&nums[j]==nums[j+1]) ++j;
            }
            while(i<nums.size()-3&&nums[i]==nums[i+1]) ++i;
        }
        return vec;
    }
};
##总结
转化为求两数之和的问题，降低复杂度。