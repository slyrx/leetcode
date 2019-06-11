## 单词
+ splicing 衔接

## 关键点
+ 临时指针和返回指针可以先随便new一个节点，这样可以利用next指针。而赋值成None就没办法用了。
+ 有一个链表有剩余如何处理？
```
start.next = l1 if l1 else l2
```


## 问题
+ 返回点指针如何定义
+ mergeTwoLists如何return
+ 答案是使用迭代写的
+ 是不是能用递归实现呢？


## 答案
```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def mergeTwoLists(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        start = result = ListNode(0)
        
        while(l1 and l2):
            if l2.val > l1.val:
                start.next, l1 = l1, l1.next
            else:
                start.next, l2 = l2, l2.next
            
            start = start.next
        
        start.next = l1 if l1 else l2
            
        return result.next

```
