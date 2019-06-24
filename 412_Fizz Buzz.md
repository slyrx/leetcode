## 目标
+ 3及3的倍数输出Fizz
+ 5及5的倍数输出Buzz
+ 3和5的倍数输出FizzBuzz

## 思路
+ 从1开始
+ 对数整除的表现是余数为0，i%3==0

## 答案
```
class Solution(object):
    def fizzBuzz(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        ans = []
        for i in xrange(1,n+1):
            if i%3 == 0 and i%5 == 0:
                ans.append("FizzBuzz")
            elif i%3 == 0:
                ans.append("Fizz")
            elif i%5 == 0:
                ans.append("Buzz")
            else:
                ans.append(str(i))
            
        return ans
```
