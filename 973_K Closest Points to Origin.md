## 题意
给出二维数组表示的点的集合，和k个数量，求距离圆点最近的k个点

## 输入
二维数组和整型

## 输出
二维数组

## 答案代码
```
class Solution(object):
    def kClosest(self, points, K):
        '''
        :type points: List[List[int]]
        :type K: int
        :rtype: List[List[int]]
        '''
        
        dic = {}
        
        for x, y in points:
            dic[(x, y)] = x**2+y**2
        
        distances = sorted(dic.items(), key=lambda x:x[1])
    
        res = []
        for i in distances[:K]:
            res.append(i[0])
        
        return res
            
```
