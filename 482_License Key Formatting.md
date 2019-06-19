## 目标
+ 一串只包含字母和中划线的字符串
+ 给一个数字n，
+ 重新格式化字符串，使得原字符以k为间隔
+ 右对齐
+ 重新显示字符串

## 思路
+ 从后向前分割
+ 选择截取的对象
+ 截取对象重新填入到数组中

## 答案
```
class Solution(object):
    def licenseKeyFormatting(self, S, K):
        """
        :type S: str
        :type K: int
        :rtype: str
        """
        
        str1 = S
        str1 = str1.replace("-","").upper()
        lenstr = len(str1)
        
        if lenstr <= 0:
            return str1
        l = [str1[max(i-K,0):i] for i in range(lenstr, 0, -K)]
        return "-".join(l[::-1])
        
```
