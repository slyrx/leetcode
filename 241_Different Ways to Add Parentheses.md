## 题意
给出一个式子，向其中添加圆括号，输出所有可能等式的结果到一维数组

## 输入
字符串

## 输出
一维数组

## 答案代码
```
class Solution(object):
    def diffWaysToCompute(self, input):
        '''
        :type input: str
        :rtype: List[int]
        recursive with memoization
        collect operators
        collect numbers
        cut the equation into two
        recurse until you hit one number and return that number
        '''
        numbers = []
        operations = []
        
        def parse(input):
            currVal = 0
            for char in input:
                if char == '+':
                    numbers.append(currVal)
                    currVal = 0
                    operations.append('+')
                elif char == '-':
                    numbers.append(currVal)
                    currVal = 0
                    operations.append('-')
                elif char == '*':
                    numbers.append(currVal)
                    currVal = 0
                    operations.append('*')
                else:
                    currVal *= 10
                    currVal += int(char)
            numbers.append(currVal)
        parse(input)
        def eva(leftVal, rightVal, operation):
            if operation == '+':
                return leftVal + rightVal
            elif operation == '-':
                return leftVal -  rightVal
            else:
                return leftVal * rightVal
        memo = dict()
        def rec(start,end):
            if (start,end) in memo:
                return memo[(start,end)]
            if start == end:
                return [numbers[start]]
            ans = []
            for i in range(start,end):
                left = rec(start,i)
                right = rec(i+1,end)
                for leftVal in left:
                    for rightVal in right:
                        ans.append(eva(leftVal,rightVal,operations[i]))
            memo[(start,end)] = ans
            return ans
        
        return rec(0,len(numbers)-1)[::-1]
```
