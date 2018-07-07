#题目
最后一个单词的长度
## 问题： 
给定一个仅包含大小写字母和空格 ' ' 的字符串，返回其最后一个单词的长度。
如果不存在最后一个单词，请返回 0 。
## 编程实现：
class Solution {
public:

    int lengthOfLastWord(string s) 
    {
        int len1=0;
        for(int i=s.size()-1;i>=0;)
        {
            while(i>=0 && s[i]==' ')
            {
                i--;
            }
            while(i>=0 && s[i]!=' ')
            {
                len1++;
                i--;
            }
            break;
        }
        return len1;
    }
};
##总结
从后往前遍历一遍字符串，遇到空格继续向前遍历，若遇到非空格len1加一，继续向前遍历，再遇到空格或者遍历结束，退出循环，返回单词的长度。
