#题目
种花问题
## 问题： 
假设你有一个很长的花坛，一部分地块种植了花，另一部分却没有。可是，花卉不能种植在相邻的地块上，它们会争夺水源，两者都会死去。

给定一个花坛（表示为一个数组包含0和1，其中0表示没种植花，1表示种植了花），和一个数 n 。能否在不打破种植规则的情况下种入 n 朵花？能则返回True，不能则返回False。
## 编程实现：
class Solution {
public:
    bool canPlaceFlowers(vector<int>& flowerbed, int n) {
        int i = 0;
         int count = 0;
          while (i < flowerbed.size()) 
         {
              if ((flowerbed[i] == 0) && (i == flowerbed.size() - 1 || flowerbed[i + 1] == 0) && (i == 0 || flowerbed[i - 1] == 0)) 
             { 
                  flowerbed[i] = 1;
                  count++;
             }
             i++;
         }
         if (count >= n) 
             return true;
         return false;
    }
};
##总结
遍历数组，如果到i时前后都为0，就将i处值改为1，并且统计修改的个数，遍历数组结束后将统计的个数跟n比较，如果个数大于或等于n则返回true，否则返回false。