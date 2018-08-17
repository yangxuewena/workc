#题目
完美数
## 问题：
#### 
对于一个 正整数，如果它和除了它自身以外的所有正因子之和相等，我们称它为“完美数”。

给定一个 正整数 n， 如果他是完美数，返回 True，否则返回 False
## 编程实现：
```C++
class Solution {
public:
    bool checkPerfectNumber(int num) 
    {
       if(num==1)                  
        return false;                   
        int ans=1;                          
        for(int i=2;i<=sqrt(num);i++)
        {
            if(num%i==0)
                ans+=i+num/i;               
        }
        return ans==num;  }                  
};
```
## 总结体会：
数sum的因子出现在1到sqrt（sum），通过for循环找出因子，每次累加两个因子，当循环到sqrt（num）时就求完所有因子的和，与原数据比较即可。