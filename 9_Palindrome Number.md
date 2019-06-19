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
