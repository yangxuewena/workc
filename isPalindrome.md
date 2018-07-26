#题目
验证回文串
## 问题：
#### 
给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。
## 编程实现：
class Solution {
public:

    bool isPalindrome(string s) 
    {
        int l=0;
        int r=s.size()-1;
        while(l<r)
        {
            if(!( (s[l]>='a' && s[l]<='z') || (s[l]>='A' && s[l]<='Z') || (s[l]>='0' && s[l]<='9')))
            {
                l++;
                continue;
            }
            if(!( (s[r]>='a' && s[r]<='z') || (s[r]>='A' && s[r]<='Z') || (s[r]>='0' && s[r]<='9')))
            {
                r--;
                continue;
            }
            if(s[l]>='a'&&s[l]<='z')
            {
                if((s[l]!=s[r]+'a'-'A') && s[l]!=s[r])
                {
                    return false;
                }
                
            }
            else if(s[l]>='A'&&s[l]<='Z')
            {
                if((s[l]!=s[r]-'a'+'A') && s[l]!=s[r])
                {
                    return false;
                }
                
            }
            else
            {
                if(s[l]!=s[r])
                {
                    return false;
                }
                
            }
            l++;
            r--;
            
        }
        return true;
    }
};
## 总结体会：
分别从两端遍历，若不是字母和数字则跳过，若左端是小写字母判断右端是否是与之相对应的大写或小写字母;若左端是大写字母同样;若左端是数字判断右端是否是与之相同的数字,不是返回false,遍历结束返回true。