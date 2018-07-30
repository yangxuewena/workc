#题目
最后一个单词的长度
## 问题： 
给定一个仅包含大小写字母和空格 ' ' 的字符串，返回其最后一个单词的长度。

如果不存在最后一个单词，请返回 0 。
## 编程实现：
```C++
class Solution {
public:

    int lengthOfLastWord(string s) {
        int len1;
        int len2;
        if(s.size()==0)
            return 0;
        for(int i=s.size()-1;i>=0;i--)
        {
            if(s[i]!=' ')
            {
                len1=i;
                break;
            }
            if(i==0) 
                return 0;
        }
        if(len1==0&&s[0]!=' ')
            return 1;
        else if(len1==0&&s[0]==' ')
            return 0;
        for(int j=len1;j>=0;j--)
            if(s[j]==' ')
            {
                len2=j;
                return len1-len2;
            }
            else if(j==0)
                 return len1-len2+1; 
    }
};
```
##总结
从后向前查找空格位置，当遇到第一个字母时记录位置，遇到第一个空格或者到达字符串第一个字符时记录位置，两者相减。