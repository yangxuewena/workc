#题目
删除链表中的结点
## 问题： 
删除链表中等于给定值val的所有结点
## 编程实现：
class Solution(object):

    def removeElements(self, head, val):
        """
        :type head: ListNode
        :type val: int
        :rtype: ListNode
        """
        pre_node = ListNode(None)
        pre_node.next = head
        q = pre_node
        while q.next:
            if q.next.val == val:
                q.next = q.next.next
            else:
                q = q.next
        return pre_node.next
        
##总结
在链表首段接上一个空结点，遍历一遍链表，若值等于val,指向下一个结点再判断；若不等于val,直接跳到下一个结点。