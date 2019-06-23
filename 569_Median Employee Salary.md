## 目标
+ 每个公司部门的工资中位数


## 知识点
+ 中位数的频率应该等于或大于阵列中较大元素和小元素的绝对差值，无论它是否具有奇数或偶数量以及它们是否是不同的。
+ SIGN的作用
+ + 如果 number > 0, 返回 1
+ + 如果 number = 0, 返回 0
+ + 如果 number < 0, 返回 -1


## 答案
```
SELECT
    Employee.Id, Employee.Company, Employee.Salary
FROM
    Employee,
    Employee alias
WHERE
    Employee.Company = alias.Company
GROUP BY Employee.Company , Employee.Salary
HAVING SUM(CASE
    WHEN Employee.Salary = alias.Salary THEN 1
    ELSE 0
END) >= ABS(SUM(SIGN(Employee.Salary - alias.Salary)))
ORDER BY Employee.Id
;
```
