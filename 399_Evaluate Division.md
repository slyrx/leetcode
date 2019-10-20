## 思路
1. 先将已知的式子存成字典
+ 字典的形式是：每个元素和其他元素的对应关系
2. 再遍历要查询的式子在字典里进行查找返回结果。
+ 用一个队列来表示式子，式子中出现过的元素都进入到队列中去。
+ 用一个 set 来记录元素访问情况，避免元素进入循环状态。
+ 在查询的过程中，就是实现等式从左向右递等的过程。这个递等就是通过累乘来实现的，所以在填入一次式子元素时，就需要用 product * d 来实现一次累乘。

## 关键
1. graph 里的 d 表示什么？
2. product * d 表示什么？
3. 使用了特殊的数据结构 collections 里面的 defaultdict(list),括号中间是字典后面跟随元素的类型

## 涉及的情况
只有一种情况，且会涉及到边界情况，就是查询元素不存在字典中该如何处理。此处是返回 -1。

## 答案
```
class Solution(object):
    def calcEquation(self, equations, values, queries):
        """
        :type equations: List[List[str]]
        :type values: List[float]
        :type queries: List[List[str]]
        :rtype: List[float]
        """
        graph = collections.defaultdict(list)
        
        def iniGraph(equations, values):
            for ver, val in zip(equations, values):
                c, p = ver
                graph[c].append((p, val))
                graph[p].append((c, 1/val))
        
        def findPath(b, e):
            if b not in graph or e not in graph:
                return -1
            
            q = collections.deque()
            visited = set()
            
            q.append((b, 1.0))
            while q:
                front, product = q.popleft()
                if front == e:
                    return product
                visited.add(front)
                for n, d in graph[front]:
                    if n not in visited:
                        q.append((n, product*d))
                        
            return -1
        iniGraph(equations, values)
        return [findPath(b, e) for b, e in queries]
```
