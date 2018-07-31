#题目
整数转罗马数字
## 问题： 
给定一个整数，将其转为罗马数字。输入确保在 1 到 3999 的范围内。
## 编程实现：
class Solution {
public:

    string intToRoman(int num)
    {
        string i[10]={"","I","II","III","IV","V","VI","VII","VIII","IX"};
        string x[10]={"","X","XX","XXX","XL","L","LX","LXX","LXXX","XC"};
        string c[10]={"","C","CC","CCC","CD","D","DC","DCC","DCCC","CM"};
        string m[4]={"","M","MM","MMM"};
       return m[num/1000]+c[num%1000/100]+x[num%100/10]+i[num%10];
    }
};
##总结
分别表出个位，整十，整百，整千的罗马表示法，然后对给定的数字依次取出每一位，与之对应即可。