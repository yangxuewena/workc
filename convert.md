#题目
Z字形变换
## 问题： 
将字符串 "PAYPALISHIRING" 以Z字形排列成给定的行数
## 编程实现：
class Solution {
public:

    string convert(string s, int numRows)
    {
        int len = s.length();
        int nodeLen = 2*numRows-2;
        string result = "";
        if (len == 0 || numRows == 0 || numRows == 1)
            return s; 
        for (int i = 0; i < numRows; i++)
            for (int j = i; j < len; j += nodeLen) 
            {
                result += s[j];
                if (i != 0 && i != numRows-1 && j - 2*i + nodeLen < len)
                    result += s[j - 2*i + nodeLen];
            }
        return result;
    }
};
##总结
第一行和最后一行的字母下标数，可以看成一个等差数列，中间的几行也有规律。把满列的和单列的分成两部分来看，满列的按等差数列来做，单列的用单列的规律加进去。