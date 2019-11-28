## 题意
给出一个 hh:ss 的时间格式，按照其中数字元素，给出能表示的次大时间表示。可以重复使用元素。

## 输入
字符串

## 输出
字符串

## tips
+ set() 解析数字字符串时，结果会变成独立的字符串数组。
+ 两个 set() 比较表示什么？ set(s) <= set(t) 表示集合 s 中元素都在 t 集合中

## 答案代码
```
class Solution(object):
    def nextClosestTime(self, time):
        """
        :type time: str
        :rtype: str
        """
        h, m = time.split(":")
        curr = int(h) * 60 + int(m)
        result = None
        for i in xrange(curr+1, curr+1441):
            t = i % 1440
            h, m = t // 60, t % 60
            result = "%02d:%02d" % (h, m)
            if set(result) <= set(time):
                break
        return result

```
