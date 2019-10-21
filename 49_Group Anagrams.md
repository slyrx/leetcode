## 单词
anagrams 同字母异序词

## 思路
遍历数组中的每个字符串单词，将每一个字符串单词排序，作为关键字放入预设的字典中，同时将被检查的字符串作为元素追加到对应的数组中。

## 关键
1. 把字符串数组作为字典类型 dict 的关键字时，需要将字符串类型转换成 tuple()
2. 快速的返回字典对应 values 值的方法是 dict.values()

## 涉及情况
不涉及边界情况

## 答案
```
class Solution(object):
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        
        dd = collections.defaultdict(list)
        
        for s in strs:
            dd[tuple(sorted(s))].append(s)
            
        return dd.values()
```


