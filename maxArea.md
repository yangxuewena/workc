#题目
盛最多水的容器
## 问题： 
给定 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。
## 编程实现：
class Solution {
public:
    int maxArea(vector<int>& height) 
    {
        int l=0;
        int r=height.size()-1;
        int maxw=0;
        while(l<r)
        {
            int v=min(height[l],height[r])*(r-l);
            if(v>maxw)
            {
                maxw=v;
            }
            if(height[l]>height[r])
            {
                r--;
            }
            else
            {
                l++;
            }
        }
        return maxw;
    }
};
##总结
维护两个指针f、l分别指向数组左右两端，则f和l构成的容器盛水体积计算公式为min(height[f],height[l])*(l-f)。可以看出盛水体积取决于容器边中较小的数字和容器底长度。若移动较大的数字，则容器底长度会变小，而盛水的最大高度不变，所以盛水体积不会变更大。因此需要移动两数中较小的数字，这样若中间出现特别大的数字，则有可能提高盛水体积。然后每次移动完更新此时的最大盛水体积，直到两指针相遇。