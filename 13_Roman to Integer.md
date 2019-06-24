## 目标
把罗马数字转换成int数字

## 思路
+ 需要知道罗马数字的原理
规则：
1. 字母相加表示和
2. 通常从左向右的顺序也是从大到小的字母顺序
3. - 特殊的V和X的左边可以放小的I
   -      L和C的左边可以放小的X
   -      D和M的左边可以放小的C
4. 如"MCMXCIV"中，有特殊的字符组合，则优先处理特殊的组合情况

## 答案
```
class Solution(object):
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        ans = 0
        dic = {
               "I": 1,
               "V": 5,
               "X": 10,
               "L": 50,
               "C": 100,
               "D": 500,
               "M": 1000,
              }
        
        if "IV" in s:
            ans += 4
            s = s.replace("IV", "")
        if "IX" in s:
            ans += 9
            s = s.replace("IX", "")
        if "XL" in s:
            ans += 40
            s = s.replace("XL", "")
        if "XC" in s:
            ans += 90
            s = s.replace("XC", "")
        if "CD" in s:
            ans += 400
            s = s.replace("CD", "")
        if "CM" in s:
            ans += 900
            s = s.replace("CM", "")
        for i in xrange(len(s)):
            if s[i] in dic:
                ans += dic[s[i]]
        
        return ans
            
```
