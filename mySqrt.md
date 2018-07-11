#题目
x的平方根
## 问题： 
实现 int sqrt(int x) 函数。

计算并返回 x 的平方根，其中 x 是非负整数。

由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。
## 编程实现：
class Solution {
public:

    int mySqrt(int x) 
    {
        if (x <= 0) return 0;
        int left = 1, right = x, mid = left + (right - left) / 2;
        while (left <= right) {
            if (mid == x / mid) return mid;
            else 
            {
                if (mid > x / mid) right = mid - 1;
                else left = mid + 1;
                mid = left + (right - left) / 2;
            }
        }
        return right;
        
    }
};
##总结
使用二分法进行查找。