#题目
电话号码的字母组合
## 问题： 
给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。
给出数字到字母的映射如下（与电话按键相同）。
## 编程实现：
class Solution {
public:

    vector<string> letterCombinations(string digits) 
    {
        vector<string> ret;
        if(digits == "")
            return ret;
            
        ret.push_back("");
        
        vector<string> dict(10); //0~9
        dict[2] = "abc";
        dict[3] = "def";
        dict[4] = "ghi";
        dict[5] = "jkl";
        dict[6] = "mno";
        dict[7] = "pqrs";
        dict[8] = "tuv";
        dict[9] = "wxyz";
        
        for(int i = 0; i < digits.size(); i ++)
        {
            int size = ret.size();
            for(int j = 0; j < size; j ++)
            {
                string cur = ret[0];
                ret.erase(ret.begin());
                for(int k = 0; k < dict[digits[i]-'0'].size(); k ++)
                {
                    ret.push_back(cur + dict[digits[i]-'0'][k]);
                }
            }
        }
        return ret;      
    }
##总结
枚举所有情况，
对于每一个输入数字，对于已有的排列中每一个字符串，分别加入该数字所代表的每一个字符，
所有是三重for循环。