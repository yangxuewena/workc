#题目
数组拆分 I
## 问题： 
给定长度为 2n 的数组, 你的任务是将这些数分成 n 对, 例如 (a1, b1), (a2, b2), ..., (an, bn) ，使得从1 到 n 的 min(ai, bi) 总和最大。
## 编程实现：
class Solution {
public:

    int arrayPairSum(vector<int>& nums) {
        int res = 0, n = nums.size();
        sort(nums.begin(), nums.end());
        for (int i = 0; i < n; i += 2) {
            res += nums[i];
        }
        return res;
    }
};

##总结
将数组排序，保证每组数差最小，将每组中的最小值取出，相加即可得到最大值。