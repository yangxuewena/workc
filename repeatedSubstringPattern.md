#题目
重复的子字符串
## 问题： 
给定一个非空的字符串，判断它是否可以由它的一个子串重复多次构成。给定的字符串只含有小写英文字母，并且长度不超过10000。
## 编程实现：
```C++
class Solution {
public:
    bool repeatedSubstringPattern(string s) {
        int n=s.size();
        if(n<2)
            return false;
        for(int i=1;i<n;i++)
        {
            int flag=0;
            if(n%i!=0)
                continue;
            for(int j=0;j<n-i;j++)
            {
                if(s[j]!=s[j+i])
                {
                    flag=1;
                    break;
                }
            }
            if(flag==0)
                return true;
        }
        return false; 
    }
};
```
##总结
字符串的长度能整除构造子串长度，且构造子串长度一定小于原字符串长度，这样可以减少循环次数。然后按一种构造子串长度，判断字符串串中对应位置的字符是否相同，如果不相同，对下一种长度进行搜索，如果对应位置都相等则返回true。