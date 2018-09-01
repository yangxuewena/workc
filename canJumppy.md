#题目
跳跃游戏
## 问题： 
给定一个数组，你位于数组的第一个位置，判断你能否到达最后位置
## 编程实现：
class Solution {
  public:
      bool canJump(vector<int>& nums) {
          if(nums.empty())
              return false;
          int size=nums.size();
          int far=-1;
          for(int i=0;i<size;i++){
              if(nums[i]>far)
                 far=nums[i];
             if(far>=size-i-1)
                 return true;
             if(far==0)
                 break;
             far--;
         }
         return false;
     }
};
        
##总结
从第一个数开始遍历，保存一个far值为跳跃长度，对每个位置，判断长度是否大于far,大于则更新为当前数字，判断是否能到达最后位置，能返回true，判断far，是否为0，为0停止遍历，返回FALSE。