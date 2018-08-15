#题目
找到所有数组中消失的数字
## 问题： 
给定一个范围在  1 ≤ a[i] ≤ n ( n = 数组大小 ) 的 整型数组，数组中的元素一些出现了两次，另一些只出现一次。

找到所有在 [1, n] 范围之间没有出现在数组中的数字。

您能在不使用额外空间且时间复杂度为O(n)的情况下完成这个任务吗? 你可以假定返回的数组不算在额外空间内。
## 编程实现：

class Solution {
public:

    vector<int> findDisappearedNumbers(vector<int>& nums) {
        for (auto num : nums) {
            int index = num > 0 ? num : -num;
            index--;
            if (nums[index] > 0) {
                nums[index] = -nums[index];
            }
        }
        vector<int> result;
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] > 0) {
                result.push_back(i + 1);
            }
        }
        return result;
    }
};

##总结
遍历数组，把与元素值相等的那个索引对应的值赋值为相反数，再次遍历，如果某个索引对应的元素值是正数，就说明与这个索引相同的值在数组中不存在，返回即可。