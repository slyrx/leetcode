## 目标
以字符串的方式实现二进制加法

## 思路
+ stop的位置总要多出来一个，不论是正序还是倒序
+ 字符串做加法的时候，需要将所有元素右移，标准化
+ 字符串:
  + 从左面加，右对齐, str + result
  + 从右面加，左对齐,       result + str

## 问题
1. 去a和b两者之间最大的字符串长度，max(len(a), len(b))
2. zfill的使用方法，参数填标准化的长度。a.zfill(max_len)

## 答案
```
class Solution(object):
    def addBinary(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        max_len = max(len(a), len(b))
        a = a.zfill(max_len)
        b = b.zfill(max_len)
        
        temp_sum  = 0
        carry = 0
        
        result = ""
        for i in xrange(max_len - 1, -1, -1):
            temp_sum = int(a[i]) + int(b[i]) + carry
            carry = 0
            
            if temp_sum >= 2:
                carry = 1
            
            temp_sum = 1 if temp_sum % 2 else 0
            
            result = str(temp_sum) + result
        
        if carry == 1:
            result = str(carry) + result
            
        return result
```
