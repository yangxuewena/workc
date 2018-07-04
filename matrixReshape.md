#题目
重塑矩阵
## 问题： 
在MATLAB中，有一个非常有用的函数 reshape，它可以将一个矩阵重塑为另一个大小不同的新矩阵，但保留其原始数据。
给出一个由二维数组表示的矩阵，以及两个正整数r和c，分别表示想要的重构的矩阵的行数和列数。
重构后的矩阵需要将原始矩阵的所有元素以相同的行遍历顺序填充。
如果具有给定参数的reshape操作是可行且合理的，则输出新的重塑矩阵；否则，输出原始矩阵
## 编程实现：
class Solution {
public:

    vector<vector<int>> matrixReshape(vector<vector<int>>& nums, int r, int c) 
    {
        int origin_r = nums.size();
        int origin_c = nums[0].size();
        int n = origin_c*origin_r;//元素个数
        if (n == r*c) {
            //新矩阵
            vector<vector<int>> newMaxtrix(r, vector<int>(c, 0));
            for (int i = 0; i < n; i++)
                newMaxtrix[i / c][i%c] = nums[i / origin_c][i%origin_c];
            return newMaxtrix;
        }
        else
            return nums;
    }
};
##总结
先算出所给矩阵的元素个数，若与新矩阵的元素个数不一致，即直接返回原矩阵，若相等将原矩阵数据填到新矩阵中去，返回。