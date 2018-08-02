#题目
检测大写字母
## 问题： 
给定一个单词，你需要判断单词的大写使用是否正确。

我们定义，在以下情况时，单词的大写用法是正确的：

全部字母都是大写，比如"USA"。
单词中所有字母都不是大写，比如"leetcode"。
如果单词不只含有一个字母，只有首字母大写， 比如 "Google"。
否则，我们定义这个单词没有正确使用大写字母
## 编程实现：
class Solution {
public:

    bool detectCapitalUse(string word) 
    {
        int count = 0;
        for(int i = 0;i <word.size();i++)
        {
            if(word[i]>='A' && word[i]<='Z')
                count ++;
        }
        if(count == word.size()  || (count==1&&(word[0]>='A'&&word[0]<='Z'))  || count ==0)
        {
            return true;
        }
        else
            return false;
    }
};
##总结
首先通过遍历字符串查找大写字母的个数，然后判断只有第一个为大写字母，或者全部为大写字母，或没有大写字母返回true，其他情况返回false。