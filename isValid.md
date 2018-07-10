#题目
有效的括号
## 问题： 
给定一个 32 位有符号整数，将整数中的数字进行反转。
## 编程实现：
class Solution {
public:

    bool isValid(string s) 
    {
        if(s.empty()) return true;
    stack<char> sta;
    for(int i=0;i<s.size();i++)
    {
        if(s[i]=='(' || s[i]=='[' || s[i]=='{')
        {
            sta.push(s[i]);
        }
        else if(sta.empty())
        {
            return false;
        }
        else if((s[i] == ')' && sta.top()=='(') ||(s[i] == ']' && sta.top()=='[')||(s[i] == '}' && sta.top()=='{'))
        {
            sta.pop();
        }
        else
            return false;
    }
    if(sta.empty())
        return true;
    else
        return false;
        
        
    }
};
##总结
首先判断字符串是否为空，如果为空，直接认为是有效字符串，返回true；然后利用stack的数据结构来解题，逐个判断字符串，如果是左括号，就打入栈中，如果是右括号，判断栈是否为空，为空则返回false，再判断栈顶是不是对应的左括号，如果是，则将栈顶的元素出栈，如果不是，则返回false。