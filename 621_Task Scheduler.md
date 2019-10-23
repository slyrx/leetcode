## 思路
先预设一个间隔宽，最大相同元素数量的矩阵，因为间隔表示的是中间夹的内容，所以实际矩阵的间隔应该为间隔+1。这时，认为其余的元素都要用来尽量填充这个矩阵，当全部填好了，剩余还有空位就用 idle 来填满。这样就是能看到的最小的间隔。

如果列表的长度比这样排出来的矩阵还大，那么就应为列表不添加任何 idle 就可以完成排列，因此最大就是自己。

## 关键
+ 有 idle 时的矩阵
+ 计算方法：（m -1）\*（n+1）+ l
+ m 的 -1 正代表了 l， n 后面的 +1 代表了包括间隔的长度。
+ 无 idle 的自己

## 涉及的情况
涉及到两种情况：
+ 需要加 idle
+ 不需要加 idle
+ 特殊情况：如果总数是大于加 idle 的情况的，那么，就认为肯定能按照间隔分配开。

## 答案
```
class Solution(object):
    def leastInterval(self, tasks, n):
        """
        :type tasks: List[str]
        :type n: int
        :rtype: int
        """
        
        dic = collections.defaultdict(int)
        
        for i in tasks:
            dic[i] += 1
            
        m = max(dic.itervalues())
        l = len([k for k in dic if dic[k] == m])
        
        return max(len(tasks), ((m-1)*(n+1)+l))
```
