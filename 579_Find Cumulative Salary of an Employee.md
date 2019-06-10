## 单词
+ Cumulative 累积的
+ Schema 图解
+ clause 从句


## 规则
+ 获得前3个月逐月累计的工资之和，排除最近一个月的工资，假定是4个月
+ ID的升序显示
+ Month的降序

## 重点
+ 体现“累积”<br>
体现累积的方式是，1月就自己，2月包括1月和2月，3月包括1月、2月和3月。

## 需要确定用那种表的形式处理？笛卡尔积还是浮动表？
+ 在同一个表中，要统计同一列的不同情况的值，用笛卡尔积比较好。虽然占用了空间，但是在运算比较上节省了时间。

## 需要假设当前的表中最多有4个月
+ 

## 需要确认join默认是谁在右边，谁在左边
+ From的表在左边
+ join的表在右边
+ 之后join的表依次在右边
+ left join意为保留左边的，而不是从左边合并。

## join默认是不是inner join?
+ 默认是内连接即join=inner join。

## 问题
+ left join需要使用on，否则会报语法错误
+ join可以不使用on，不报语法错误
+ full outer join Employee as t2这句话语法错到哪儿了？ <br>
mySql不支持full outer操作.<br>
因此，需要通过left join + right join的方式解决。
```
select * from a left outer join b
on a.id = b.id
union
select * from a right outer join b
on a.id = b.id
```
+ left outer 和 left一样
+ 显示左面月份比右面月份大1的方法，E2.month = E1.month - 1


## 答案
```
select t1.id, t1.month, (ifnull(t1.salary, 0) + ifnull(t2.salary, 0) + ifnull(t3.salary, 0)) as Salary
from 

(select id, max(month) as month
from Employee
group by id
having count(*) > 1) as maxmonth

left join Employee as t1
on (maxmonth.id = t1.id and maxmonth.month > t1.month)
left join Employee as t2
on (maxmonth.id = t2.id and t1.month -1 = t2.month)
left join Employee as t3
on (maxmonth.id = t3.id and t2.month - 1 = t3.month)
order by id asc, month desc
```

## 关键的一步是动态的算出当前表中的最大月份，再以该月份组成的表来拼接后续的表。
(select id, max(month) as month
from Employee
group by id
having count(*) > 1) as maxmonth
