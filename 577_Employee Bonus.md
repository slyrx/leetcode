## 目标
+ 选出奖金小于1000的员工名
+ 没有奖金的人也要列出，填成null

## 答案
```
select t1.name, t2.bonus
from Employee as t1
left join Bonus as t2
on t1.empId = t2.empId
where t2.bonus < 1000 or t2.bonus is null
```

