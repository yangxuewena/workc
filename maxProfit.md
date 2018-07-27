#题目
买卖股票的最佳时机 II
## 问题：
给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。
设计一个算法来计算你所能获取的最大利润。你可以尽可能地完成更多的交易（多次买卖一支股票）。
注意：你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。
## 编程实现：
class Solution {
public:

    int maxProfit(vector<int>& prices) {
       int m = 0;
        for (int i = 1; i < prices.size(); i++) 
            if (prices[i] > prices[i - 1]) 
                m += prices[i] - prices[i - 1];
        return m; 
    }
};

##总结
设m初值为0，从第二天开始判断，只要后一天的价格大于前一天的，就计算利润，数组遍历结束即可求出最大利润。