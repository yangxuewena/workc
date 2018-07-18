#题目
寻找重复数
## 问题： 
给定一个包含 n + 1 个整数的数组 nums，其数字都在 1 到 n 之间（包括 1 和 n），可知至少存在一个重复的整数。假设只有一个重复的整数，找出这个重复的数。
## 编程实现：
class Solution {
public:

    int findDuplicate(vector<int>& nums) {
         int high=nums.size()-1;
        int low=0;
        while(high>low){
        	int mid=(high+low)/2;
        	int count=0;
        	for(int i=0;i<nums.size();i++)
            {
        		if(nums[i]<=mid)
        			count++;
        	}
        	if(count>mid)
        		high=mid;
        	else
        		low=mid+1;
        }
        return low;
    }
};
##总结
本题考虑用二分法，在区间[1, n]中搜索，首先求出中点mid，然后遍历整个数组，统计所有小于等于mid的数的个数，如果个数大于mid，则说明重复值在[mid+1, n]之间，反之，重复值应在[1, mid-1]之间，然后依次类推，搜索完成后，此时的low就是要求的重复值。