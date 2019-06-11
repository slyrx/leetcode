 
## 思路
+ 建立一个栈
+ 遍历字符串数组s，
+ 遇到左括号就入栈
+ 遇到右括号就出栈
+ 最后检查是否还是空栈，如果是空栈就返回配对，否则不配对。

## 配对逻辑不清晰
+ 我考虑了一种括号之间互相嵌套的情况
+ 嵌套的情况会不会影响？
不会
+ 考虑括号里会有别的内容，如字母之类的。
题意里已经说明只有括号。


## 错误代码
```
        stack = []
        left_parentheses = {")":"(","[":"]","{":"}"}
        for i in s:
        
            if i in left_parentheses:
                print stack, left_parentheses[i]
                stack.pop(left_parentheses[i])
            stack.append(i)
            
        return not stack
```
+ 主要是if段的逻辑有问题
```
            if i in dic:
                elem = stack.pop() if stack else "#"
                if dic[i] == elem:
                    continue
                else:
                    return False
```
+ 如果stack中存在字符，则将栈顶的内容弹出。
+ 弹出的内容和当前字符的字典键值比较，如果相同，则继续下一个判断
+ 否则返回不匹配。
+ **栈顶元素一定是不匹配，或者字典值的匹配左括号**。
