## 目标
+ 给出一个32位的带符号的整型
+ 将这个整数的位数调转
+ 有负号的保留负号

## 思路
+ 检查整数是否为负数？
+ python默认是64位的，因此可以通过这种方式来检测

## 答案
```
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        sign_flag = False
        
        if x < 0:
            sign_flag = True
            x = abs(x) # key
        
        rev = 0
        while x:
            pop  = x % 10
            rev = rev * 10 + pop
            x = x / 10
    
        if sign_flag:
            rev = -rev
    
        if rev < (-2**31) or rev >(2 ** 31 - 1): # key
            return 0                             # key
       
        return rev

```
