## 思路
+ 递归
+ 找到最后一个元素，令最后一个元素的指针指向前一个元素，前一个元素的指针指向None。


## 答案
```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        
        if head == None or head.next == None:
            return head
        
        pre = self.reverseList(head.next)
        head.next.next = head
        head.next = None
        
        return pre

```
