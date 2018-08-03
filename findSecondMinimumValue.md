#题目
二叉树中第二小的节点
## 问题： 
给定一个非空特殊的二叉树，每个节点都是正数，并且每个节点的子节点数量只能为 2 或 0。如果一个节点有两个子节点的话，那么这个节点的值不大于它的子节点的值。 
给出这样的一个二叉树，你需要输出所有节点中的第二小的值。如果第二小的值不存在的话，输出 -1 。
## 编程实现：

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {

public:

    int findSecondMinimumValue(TreeNode* root) {
      int first=65535,second=65535;  
        secondmin(root,first,second);  
        if(second!=65535)return second;  
        else return -1;  
    }  
    void secondmin(TreeNode *root,int &first,int &second){  
        if(root==NULL)return;  
        else{  
            if(root->val<first){  
                second=first;  
                first=root->val;  
            }  
            else if(root->val>first&&root->val<second)  
                    second=root->val;                  
            secondmin(root->left,first,second);  
            secondmin(root->right,first,second);  
        }     
    }    
};


##总结
设置两个变量传递最小值和第二小值，然后先序遍历，每到一个结点，将此结点的值与first和second比较，如果比first小，则把first的值赋给second和当前结点的值赋给first（顺序不能反）。如果比first大且比second小，则把当前结点的值赋给second。依次遍历完所有结点。最后判断second的值是否改变，不变说明没有第二小值返回-1，否则返回second值。