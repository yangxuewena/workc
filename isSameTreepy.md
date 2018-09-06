#题目
螺旋矩阵
## 问题： 
给定两个二叉树，编写一个函数来检验它们是否相同。
如果两个树在结构上相同，并且节点具有相同的值，则认为它们是相同的。
## 编程实现：
class Solution(object):

    def isSameTree(self, p, q):
        """
        :type p: TreeNode
        :type q: TreeNode
        :rtype: bool
        """
        if not p and not q:#
            return True
        if p and q and p.val==q.val:
            l=self.isSameTree(p.left,q.left)#
            r=self.isSameTree(p.right,q.right)
            return l and r#and操作，需要l与r皆为true时，才返回真。只用最后一次递归边界return值
        else:
            return False
        
##总结
两二叉树皆为空，递归边界，两者皆为空返回真，递归，每次重新从函数入口处进行，每次进行递归边界判断，and操作，需要l与r皆为true时，才返回真。只用最后一次递归边界return值。