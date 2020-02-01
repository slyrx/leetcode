## 解答代码
```
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        
        p3_head = p3 = ListNode(0)
        carry = 0
        
        while l1 != None or l2 != None or carry:
            v1 = v2 = 0
            if l1:
                v1 = l1.val
                l1 = l1.next
            if l2:
                v2 = l2.val
                l2 = l2.next
                
            carry, dig_res = divmod(v1 + v2 + carry, 10)
            p3.next = ListNode(dig_res)
            p3 = p3.next
            
        return p3_head.next
            
```
