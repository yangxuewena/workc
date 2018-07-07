#题目
使用最小花费爬楼梯
## 问题： 
数组的每个索引做为一个阶梯，第 i个阶梯对应着一个非负数的体力花费值 cost[i](索引从0开始)。
每当你爬上一个阶梯你都要花费对应的体力花费值，然后你可以选择继续爬一个阶梯或者爬两个阶梯。
您需要找到达到楼层顶部的最低花费。在开始时，你可以选择从索引为 0 或 1 的元素作为初始阶梯。
## 编程实现：
class Solution {
public:

    int minCostClimbingStairs(vector<int>& cost) 
    {
        vector<int> totol(cost.size(), 0);
        totol[0] = cost[0], totol[1] = cost[1];
        for (int i = 2; i < cost.size(); i++) 
        {
            totol[i] = min(totol[i - 2] + cost[i], totol[i - 1] +cost[i]);
        }
        return min(totol[cost.size() - 1], totol[cost.size() - 2]);
    }
};
##总结
除去前面两级台阶，每一级可以是从前一级上来的，也可以从前两级上来的。计算上到某一级的花销为totol[i],递推式为totol[i] = min(totol[i - 2] + cost[i], totol[i - 1] +cost[i])，上到顶的时候也可以是从倒数第一级上来的，也可以从倒数第二级上来的，所以最后返回min(totol[cost.size() - 1], totol[cost.size() - 2])。 