## 题意
输入一串字符串，输出规定解码规则的字符串

## 规则
按要求输出指定重复次数的字母

## 输入
字符串

## 输出
字符串

## 答案代码
```
#key: 字符串判断是数字的新函数c.isdigit(); 想要连续在一行赋值变量，需要用分号结尾，而不是逗号
class Solution(object):
    def decodeString(self, s):
        '''
        :type s: str
        :rtype: str
        '''
        stack = []; cur_num = 0; curString=''
        
        for c in s:
            if c.isdigit():
                cur_num = cur_num*10 + int(c)
            elif c == '[':
                stack.append(curString)
                stack.append(cur_num)
                curString = ''
                cur_num = 0
            elif c == ']':
                num = stack.pop()
                preString = stack.pop()
                curString = preString + num*curString
            else:
                curString += c
                
        return curString
```
