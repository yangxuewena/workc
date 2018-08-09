#题目
最接近的三数之和
## 问题： 
给定一个包括 n 个整数的数组 nums 和 一个目标值 target。找出 nums 中的三个整数，使得它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在唯一答案。
## 编程实现：
class Solution {
public:

    int threeSumClosest(vector<int>& nums, int target)
    {
        sort(nums.begin(),nums.end());
        int sum=0,close=INT_MAX,m=0,result=0;
        for(int i=0;i<nums.size()-2;++i){
            m=target-nums[i];
            int l=i+1,r=nums.size()-1;
            while(l<r){
                sum=nums[l]+nums[r];
                if(sum<m){
                    if(m-sum<close){
                        close=m-sum;
                        result=nums[i]+nums[l]+nums[r];
                    }
                    ++l;
                }
                else if(sum>m){
                    if(sum-m<close){
                        close=sum-m;
                        result=nums[i]+nums[l]+nums[r];
                    }
                    --r;
                }
                else{
                    return target;
                }
            }
        }
        return result;  
    }
};
##总结
首先我们将数组中的元素按照从小到大的顺序进行排序。其次，看最终取出的三个数中的第一个数，若数组长度为n，那么有n种取法。假设取的第一个数是A[i]，那么第二三两个数从A[i+1]~A[len]中取出。找到“第一个数为A[i]固定，后两个数在A[i]后面元素中取。并且三数之和离target最近的情况。”这时，我们用两个指针j,k分别指向A[i+1]和A[len]，如果此时三数之和A[i]+A[j]+A[k]<target，说明三数之和小了，我们将j后移一格；反之，若和大于target，则将k前移一格；直到j和k相遇为止。在这期间，保留与target最近的三数之和。一旦发现有“和等于target的情况”,立即输出即可。