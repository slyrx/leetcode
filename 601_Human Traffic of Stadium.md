## 单词
+ stadium 体育场
+ stats = statistics 统计

## 目标
+ 3个以上连续的行大于100个数量。

## 时间相减的差值是等于1吗？
+ 是

## 同一个表连from3次
+ from stadium t1, stadium t2, stadium t3
+ 表达的依然是笛卡尔积，只是没有on的附加条件


## 答案
```
select distinct t1.*
from stadium t1, stadium t2, stadium t3
where t1.people >= 100 and t2.people >= 100 and t3.people >= 100
and
(
	  (t1.id - t2.id = 1 and t1.id - t3.id = 2 and t2.id - t3.id =1)  -- t1, t2, t3
    or
    (t2.id - t1.id = 1 and t2.id - t3.id = 2 and t1.id - t3.id =1) -- t2, t1, t3
    or
    (t3.id - t2.id = 1 and t2.id - t1.id =1 and t3.id - t1.id = 2) -- t3, t2, t1
)
order by t1.id
;
```
