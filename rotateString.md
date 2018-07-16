#题目
旋转字符串
## 问题： 
给定两个字符串, A 和 B。
A 的旋转操作就是将 A 最左边的字符移动到最右边。 例如, 若 A = 'abcde'，在移动一次之后结果就是'bcdea' 。如果在若干次旋转操作之后，A 能变成B，那么返回True。
## 编程实现：
class Solution {
public:

    bool rotateString(string A, string B) 
    {
         if (A.length() != B.length()) {
            return false;
        }
        if (A == B) {
            return true;
        }
        for (int i = 0; i < A.length()-1; ++i) {
            A.push_back(A[0]);     // move the first char to the back
            A.erase(A.begin());
            if (A == B) {
                return true;
            }
        }
        return false;


    }
};
##总结
每次将A的第一个元素放到最后，再清除第一个元素，相当于将A移动一位，看此时的A与B是否相同，不相同重复操作，相同返回true.