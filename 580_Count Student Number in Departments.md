## 目标
+ 根据student和department表，统计出每个科目有多少人选择
+ 先依据dept_id统计student表中情况


## 问题
+ 列名没有一致
+ 顺序没有一致
+ 除了数量顺序意外，还需要保持字母顺序
+ + 两种顺序的独立设置方法 order by student_number desc, t2.dept_name asc


## 答案
```
select t2.dept_name, ifnull(t3.student_number, 0) as student_number
from department as t2
left join (
select t1.dept_id, count(*) as student_number
from student as t1
group by t1.dept_id
) as t3
on t3.dept_id = t2.dept_id
order by student_number desc, t2.dept_name 
```
