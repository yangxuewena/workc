#题目
丑数
## 问题：
#### 
编写一个程序判断给定的数是否为丑数。
丑数就是只包含质因数 2, 3, 5 的正整数。
## 编程实现：

class Solution {
public:
    bool isUgly(int num) {
        if (num<= 0) 
            return false;  
        if (num == 1) 
            return true;  
        while (num>= 2 &&num % 2 == 0) 
            num /= 2;  
        while (num>= 3 &&num % 3 == 0) 
            num /= 3;  
        while (num>= 5 &&num % 5 == 0) 
            num /= 5;  
        return num == 1;   
    }
};

##总结
输入数后先判断是否为0或者1，然后通过循环不断地除以2,3,5，如果最后能得到1，表示该数只包含2、3、5三个因子，返回真即可。