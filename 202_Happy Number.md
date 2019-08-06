## 思路
快慢指针的利用。

## 关键

## 涉及情况


## 答案
```
class Solution(object):
    def isHappy(self, n):
        """
        :type n: int
        :rtype: bool
        """
        def cal(n):
            x=n
            sum = 0
            while x:
                sum += (x%10)*(x%10)
                x /= 10
                
            return sum
        
        x = cal(n)
        y = cal(cal(n))
        
        while x != y:
            x = cal(x)
            y = cal(cal(y))
            
        if x == 1:
            return True
        
        return False
```
