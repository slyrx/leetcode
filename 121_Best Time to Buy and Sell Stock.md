## 单词
+ transaction 交易

## 思路
+ 需要知道某一时刻下最小的买价
+ 需要知道某一时刻最大的卖价
+ 同时要遍历每个元素，计算出每个元素对应的这两个值。
+ 同时记录下经历过的这两个值中，最大的差值。

## 关键
+ 值的初始化问题

## 问题
+ 边界没有考虑，如果是空数组，要如何处理？<br>
如果数组是空的，则直接返回0，认为没有最大获利。


## 答案
```
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        if not prices:
            return 0
        min_price = prices[0]
        max_profit = 0
        
        for i in prices:
            if i < min_price:
                min_price = i
            elif i - min_price > max_profit:
                max_profit = i - min_price
                
        return max_profit
```
