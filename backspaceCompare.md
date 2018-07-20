#题目
比较含退格的字符串
## 问题： 
给定 S 和 T 两个字符串，当它们分别被输入到空白的文本编辑器后，判断二者是否相等，并返回结果。 # 代表退格字符。
## 编程实现：
class Solution {
public:

    bool backspaceCompare(string S, string T)
    {
        string t1;
        for(int i=0; i<S.length(); i++) 
        {
            if (S[i]=='#') 
            {
                if (t1.size()) 
                    t1.pop_back();
            }
            else t1.push_back(S[i]);
        }
        string t2;
        for(int i=0; i<T.length(); i++) 
        {
            if (T[i]=='#')
            {
                if (t2.size()) 
                    t2.pop_back();
            }
            else t2.push_back(T[i]);
        }
        return t1==t2;      
    }
};
##总结
分别遍历两个字符串，利用栈，若遇到#号将前一个插入的元素删除，不是#号就压入栈，最后比较再两个新的字符串。