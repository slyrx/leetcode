## 题意
按照固定词典，对输入字符进行解读，求出解码的可能数量。

## 输入
字符串

## 输出
可能的解码方法数量

## 答案代码
```
class Solution(object):
    def numDecodings(self, s):
        '''
        :type s: str
        :rtype: int
        '''
        
        N = len(s)
        memo = [None] * N
        
        def dp(i):
            
            if i == N: return 1
            if memo[i] is not None: return memo[i]
            ans = dp(i+1) if s[i] != '0' else 0
            if s[i] != '0' and i+2<=N and int(s[i:i+2]) <= 26:
                ans += dp(i+2)
            memo[i] = ans
            return ans
        return dp(0)

```
