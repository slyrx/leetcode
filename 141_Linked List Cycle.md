## 目标
+ 确认链表中是否存在环

## 思路
+ 设置一个快，一个慢指针
+ 两者无限向前跑
+ 如果在未来遇到就说明存在环
+ 如果遇不到就说明不存在

## 答案
```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        
        if not head or not head.next:
            return False
        
        fast = head.next.next
        slow = head.next
        
        while fast != slow:
            
            if fast == None or fast.next == None:
                return False
            
            fast = fast.next.next
            slow = slow.next
        
        return True
```
