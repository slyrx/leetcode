## 思路
+ 题意：从三个表中找出没有卖东西给red公司的人
+ 关联表格是orders
+ 因此需要找在order中com_id不为red的，同时sales_id不出现在com_id为red的。
+ 体现在表中就是，将orders表和company表拼接
+ 然后以com_id为red的表做浮动表。
+ 最终的结果和salesperson拼接，求出名字
+ + 思路转换：先找出卖给red的有哪些人，再将这些人从salesperson中剔除掉。

## 问题
+ not in 如何表达？<br>
表达正确
+ 写mysql后面要加分号

## 错误答案
```
select name
from salesperson as t3
where t3.sales_id not in (select sales_id
from orders as t1
left join company as t2
on t1.com_id = t2.com_id
where t1.com_id = 1)
```
+ 差异点<br>
where条件不同
+ + 错误的：where t1.com_id = 1
+ + 正确的：where t2.name = "red"
+ 原因分析：com_id在别的表里1不一定表示red，因此要指明red就是red，不要用其他间接的判断方式，不利于以后的扩展

## 答案
```
select name
from salesperson as t3
where t3.sales_id not in (select t1.sales_id
from orders as t1
left join company as t2
on t1.com_id = t2.com_id
where t2.name = "red");
```
