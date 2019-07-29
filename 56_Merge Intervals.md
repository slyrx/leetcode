## 思路
运用了一个原理，首先对间隔的 start 进行排序，之后检查每个间隔的 end ,如果后面的 start 已经大于 end 了，那么就肯定不重合；如果出现了 start 小于 end 的情况，开始考虑比较两个间隔的 end 的情况，并将最大的间隔值进行更新。

## 关键
+ 先做排序，以间隔的 start 为依据
+ 对最大的结束端进行初始化，初始化为无穷小`-float("inf")`
+ 选择数组的最后一个元素的方法`merge[-1]`

## 排序后，可能的两种情况
+ |\_\_\_|  |\_\_\_|
+ |\_\_\_|\_\_|\_\_\_\_|

## 答案
```
class Solution(object):
    def merge(self, intervals):
        """
        :type intervals: List[List[int]]
        :rtype: List[List[int]]
        """
        
        intervals.sort(key=lambda i: i[0])
        
        merge = []
        large_end = -float('inf')
        
        for i in intervals:
            if i[0] > large_end:
                merge.append(i)
                large_end = i[1]
            elif i[1] > large_end:
                merge[-1][1] = i[1]
                large_end = i[1]
                
        return merge
```
