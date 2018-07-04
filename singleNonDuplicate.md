#题目
有序数组中的单一元素
## 问题： 
给定一个只包含整数的有序数组，每个元素都会出现两次，唯有一个数只会出现一次，找出这个数。
## 编程实现：
```C++
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        int l = 0, h = nums.size() - 1;
    while(l < h) 
    {
        int m = l + (h - l) / 2;
        if(m % 2 == 1)
            m--; 
        if(nums[m] == nums[m + 1]) 
            l = m + 2;
        else
            h = m;
    }
    return nums[l];
    }
};
```
##总结
