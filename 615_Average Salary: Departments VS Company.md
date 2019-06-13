## 目的
+ 把员工工资与平均工资比较后，改写成高、中、低的方式。


## 题目有错
+ 题中2号员工2月份的工资应该写成7000，题目中写的是6000.

## 算法思路
+ 计算出平均工资数，使用avg()函数
+ 平均工资数与员工表拼接，使用join
+ 替换关系为别的关键字标注，要使用case...when...then...else...end.


## 答案
```
select department_salary.pay_month, department_id,
case
  when department_avg>company_avg then 'higher'
  when department_avg<company_avg then 'lower'
  else 'same'
end as comparison
from
(
  select department_id, avg(amount) as department_avg, date_format(pay_date, '%Y-%m') as pay_month
  from salary join employee on salary.employee_id = employee.employee_id
  group by department_id, pay_month
) as department_salary
join
(
  select avg(amount) as company_avg,  date_format(pay_date, '%Y-%m') as pay_month from salary group by date_format(pay_date, '%Y-%m')
) as company_salary
on department_salary.pay_month = company_salary.pay_month
;
```



