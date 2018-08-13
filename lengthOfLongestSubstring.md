#题目
无重复字符的最长子串
## 问题： 
给定一个字符串，找出不含有重复字符的最长子串的长度。
示例：
给定 "abcabcbb" ，没有重复字符的最长子串是 "abc" ，那么长度就是3。
给定 "bbbbb" ，最长的子串就是 "b" ，长度是1。
给定 "pwwkew" ，最长子串是 "wke" ，长度是3。请注意答案必须是一个子串，"pwke" 是 子序列  而不是子串。
## 编程实现：
class Solution {
public:

    int lengthOfLongestSubstring(string s)
    {
        int m[256] = {0}, res = 0, left = 0;
          for (int i = 0; i < s.size(); ++i) {
              if (m[s[i]] == 0 || m[s[i]] < left) {
                  res = max(res, i - left + 1);
              } else {
                  left = m[s[i]];
             }
             m[s[i]] = i + 1;
         }
         return res;
    }
};
##总结
建立一个256位大小的整型数组，记录所有字符，定义两个变量res和left，其中res用来记录最长无重复子串的长度，left指向该无重复子串左边的起始位置，然后我们遍历整个字符串，对于每一个遍历到的字符，如果哈希表中该字符串对应的值为0，说明没有遇到过该字符，则此时计算最长无重复子串，i - left +１，最后每次都要在哈希表中将当前字符对应的值赋值为i+1。