## 思路
通过在原链中每个元素后面接着复制一个相同的节点来解决。

## 关键
+ 判空
+ 将原链中元素复制一份
+ 将随机指针的情况也复制出来
+ 将复制元素与原元素断开

## 可能存在的几种情况
+ 普通情况
![](https://discuss.leetcode.com/uploads/files/1470150906153-2yxeznm.png)
+ 只有一个节点的情况
```
{"$id":"1","next":null,"random":null,"val":-1}
```

## 问题
+ 因为前面已经对节点进行过复制，因此，在更新随机指针信息的时候，p.next.next 也会存在。

## 答案
```
"""
# Definition for a Node.
class Node(object):
    def __init__(self, val, next, random):
        self.val = val
        self.next = next
        self.random = random
"""
class Solution(object):
    def copyRandomList(self, head):
        """
        :type head: Node
        :rtype: Node
        """
        
        if not head:
            return None
        
        p = head
        while p:
            node = Node(p.val, p.next, None)
            p.next = node
            p = p.next.next
            
        p = head
        while p:
            if p.random:
                p.next.random = p.random.next
            p = p.next.next
                
        pold = head
        pnew = head.next
        presult = pnew
        
        while pnew:
            pold.next = pnew.next
            pold = pold.next
            
            if pold:
                pnew.next = pold.next
                pnew = pnew.next
            else:
                pnew = pnew.next
                
        return presult
                
```
