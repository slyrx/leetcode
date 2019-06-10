## 单词
+ pupil 小学生

## 数学知识
+ 勾股定理 确定直角三角形的
+ 确定三角形用 两边之和大于第三边

## 语句
```
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    WHEN conditionN THEN resultN
    ELSE result
END;
```

## 问题
+ case相当于一个新的属性，因此前面如果有变量的话，需要加上逗号,
```
select x, y, z   #没有逗号，报语法错误
case
    when x+y > z and x+z > y and y+z >x then "yes"
    else "no"
end as 'triangle'
from triangle
```
+ 一个sql语句后要加分号
+ 显示的属性名要和答案一摸一样，否则也会报错。


## 答案
select x, y, z,
case
    when x+y > z and x+z > y and y+z >x then "Yes"
    else "No"
end as 'triangle'
from triangle

