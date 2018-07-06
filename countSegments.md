#题目
字符串中的单词数
## 问题： 
统计字符串中的单词个数，这里的单词指的是连续的不是空格的字符。
请注意，你可以假定字符串里不包括任何不可打印的字符。
## 编程实现：
class Solution {
public:

    int countSegments(string s) 
    {
        if(s.size()==0)
			return 0;
	    int count=0;
		for(int i=0;i<s.size()-1;i++) 
        {
			if(s[i]==' ') 
            {              
					if(s[i+1]!=' ') 
                    {
						count++;
					}				
			}
		}
		if(s[0]==' ') 
        {
			count--;
		}
		return count+1;      
    }
};
##总结
统计字符串中空字符后紧跟着出现非空字符的次数来计算单词个数，最后如果字符串刚开始就出现空字符，则不用加上第一个单词，即count减一即可。
