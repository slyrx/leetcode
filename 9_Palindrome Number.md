## 题目
+ 判断给出的数字是不是回文？

## 答案1
+ 解题思路
+ + 将整型变成字符串
+ + 进行反转后与原字符串比较
```
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        
        new_x = str(x)
        y = new_x[::-1]

        return new_x == y

```

## 答案2
+ 非转换为字符串形式
+ 令我疑惑的一点是，下面这个算法还不如上面直接reverse字符串来的快，为什么不用👆上面的算法呢？
```
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        if x<0 or (x!=0 and x%10==0):
            return False
        
        reverse = 0
        while x > reverse:
            reverse = reverse * 10 + x % 10
            x /= 10
            
        return x == reverse or x == reverse / 10
```
