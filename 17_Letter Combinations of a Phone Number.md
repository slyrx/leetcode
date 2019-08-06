## 思路
手机键盘上数字映射可能出现的字母组合。使用深度遍历来解决。

## 关键
+ 提前建立键盘字典。
+ + 字典的 key 和 item 都用字符串表示
+ 设置初始条件
+ 在递归中要有：
+ + 结束条件
+ + 进一步的条件


## 涉及的情况
1. 非空的组合
主要是两方面：
+ 位置
+ 内容
检查每个位置中，不同内容的组合。
2. 空的组合

## 答案
```
class Solution(object):
    def letterCombinations(self, digits):
        """
        :type digits: str
        :rtype: List[str]
        """
        
        phone = {
            "1":"",
            "2":"abc",
            "3":"def",
            "4":"ghi",
            "5":"jkl",
            "6":"mno",
            "7":"pqrs",
            "8":"tuv",
            "9":"wxyz"
        }
        
        def helper(combination, next_digits):
            if len(next_digits) == 0:
                output.append(combination)
                return
            else:
                for letter in phone[next_digits[0]]:
                    helper(combination + letter, next_digits[1:])
        
        output = []
        if digits:
            helper("", digits)
        return output
```
