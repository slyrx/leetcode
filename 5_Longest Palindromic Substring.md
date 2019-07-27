## 思路
+ 第0个位置默认被认为是回文字符，因此预先把 max_len 设置成了1.
+ 后续的计算都是从1开始
+ for i in range(1, len(s)):
+ 从1位置开始，奇数位置的字符可以形成回文的，回文长度 max_len 加1，起始的位置以当前索引 i 减去回文长度记
+ + 厚度一次加2
+ 偶数位置的字符可以形成回文的，回文长度 max_len 加2，起始的位置以 当前索引 i 减去回文长度再减1记
+ + 厚度一次加1
+ 该思路将后续小于 max_len 的结论直接忽略掉了，只有新的超越的值才有意义


## 答案
```
class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        
        max_len = 1
        start = 0
        
        for i in range(1, len(s)):
            if (i-max_len >= 1) and (s[i-max_len-1:i+1] == s[i-max_len-1:i+1][::-1]):
                start = i-max_len-1
                max_len += 2
                
            if (i-max_len >=0) and (s[i-max_len:i+1] == s[i-max_len:i+1][::-1]):
                start = i-max_len
                max_len += 1
                
        return s[start:start+max_len]
```
