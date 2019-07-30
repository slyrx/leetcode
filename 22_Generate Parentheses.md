## 思路
通过递归的方式，对树形结构进行遍历。或者以树形的方式进行遍历。

## 关键
+ 每次递归时，传入进一步要遍历的内容
+ 需要传入初始状态

## 涉及情况
就是遍历

## 答案
```
class Solution(object):
    def generateParenthesis(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        
        def helper(curr, res, left, right):
            if len(curr) == 2*n:
                res.append(curr)
                return
            
            if left < n:
                helper(curr+"(", res, left+1, right)
            
            if right < left:
                helper(curr+")", res, left, right+1)
        
        res = []
        helper("", res, 0, 0)
        return res
```
