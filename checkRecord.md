# 题目
学生出勤纪录 I
## 问题：
#### 
给定一个字符串来代表一个学生的出勤纪录，这个纪录仅包含以下三个字符：

'A' : Absent，缺勤
'L' : Late，迟到
'P' : Present，到场
如果一个学生的出勤纪录中不超过一个'A'(缺勤)并且不超过两个连续的'L'(迟到),那么这个学生会被奖赏。

你需要根据这个学生的出勤纪录判断他是否会被奖赏。
## 编程实现：
class Solution {
public:

    bool checkRecord(string s) 
    {
        int i=0,a=0,l=0;
        while(s[i]!='\0')
        {
            
            if(s[i]=='A')
            {
                a++;
                if(a>=2)  return false; 
            }
            if(s[i]=='L') l++; 
            else l=0;
            if(l>2)  return false;            
            i++;
        }
        return true;
    }
};
## 总结体会：
遍历字符串数组，当等于A时a加1,并判断a是否大于等于2，若是返回false;等于L时l加1，不等于L时l重新赋值为0,这样就可以判断是否出现连续两个以上的L了;其余情况返回true。