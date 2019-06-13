## 单词
+ Consecutive 连续，地域上的
+ inclusive 包括的

## 目标
+ 求出所有可获得的连续的座位

## 思路
+ 空的
+ 连续的
+ 选择浮动表还是拼接表，感觉这里是需要拼接表，浮动表从逻辑上没法做。
+ 先找到最大座位号，然后开始拼接？错
+ + 替换逻辑：用两个表的拼接替换多个表的拼接。
+ + 使用的逻辑是：能够相互等价，|a-b| = |b-a|,这样就省去了拼接多张表的麻烦。
+ + ***abs()使两张表组成一个循环，避免了多个表拼接。***


## 关键
+ distinct 唯一
+ inner join
+ 顺序也要和答案的一样

## 答案
```
select distinct t1.seat_id
from cinema as t1
join cinema as t2
on abs(t1.seat_id - t2.seat_id) = 1 and (t1.free = 1) and (t2.free = 1)
order by t1.seat_id asc
```
