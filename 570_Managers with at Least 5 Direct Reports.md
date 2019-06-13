## 单词
+  direct report 直接下属

## 目的
+ 找出至少有5个下属的主管。

## 问题
+ 返回了[null],实际想要[].
+ + 应该是因为左右表导致的，区分清楚谁是主表，谁是副表即可。

## 思路
+ 先对ManagerId分组
+ 大于4个的显示


## 答案
```
select t3.Name as Name
from  (
select ManagerId, count(*)
from Employee as t1
group by ManagerId
having count(*) > 4
) as t2
join Employee as t3
on t2.ManagerId = t3.Id
```
