#题目
赎金信
## 问题：
#### 
给定一个赎金信 (ransom) 字符串和一个杂志(magazine)字符串，判断第一个字符串ransom能不能由第二个字符串magazines里面的字符构成。如果可以构成，返回 true ；否则返回 false。

(题目说明：为了不暴露赎金信字迹，要从杂志上搜索各个需要的字母，组成单词来表达意思。)
## 编程实现：
class Solution {
public:

    bool canConstruct(string ransomNote, string magazine) 
    {
        vector<int> count(26,0);                
        for(int i=0;i<magazine.size();i++)
        {
            count[magazine[i]-'a']++;
        }
        for(int j=0;j<ransomNote.size();j++)
        {
            count[ransomNote[j]-'a']--;
        }                
        for(int i=0;i<26;i++)
        {
            if(count[i]<0)
            {
                return false;
            }
        }
        return true;
    }
##总结
定义了26个整型元素的向量，且初值为0，先遍历杂志，用count记录每个字符的个数，再遍历赎金信，遍历一个字符count中对应减1，遍历count,看是否含有小于0的数，若有表示不可以构成。