## 目标
+ 在表中求下单最多的人

## 错误答案
```
select t1.customer_number
from orders as t1
group by t1.customer_number
order by t1.customer_number desc offset 1
```

## 显示group by 细节的方法
+ SELECT customer_number, COUNT(*)
+ COUNT(\*)就是对统计出来的数的表示

## 如何依据group by结果排序
+ ORDER BY COUNT(*) DESC

## 如何只取一个值
+ limit 1

## offset和limit的区别和联系
+ select * from table limit 2,1; <br>
跳过2条取出1条数据，limit后面是从第2条开始读，读取1条信息，即读取第3条数据.
+ select * from table limit 2 offset 1;  <br>
从第1条（不包括）数据开始取出2条数据，limit后面跟的是2条数据，offset后面是从第1条开始读取，即读取第2,3条
+ limit <跳过>, <条数> offset <起始> <br>
+ + <跳过>,如果没写，默认先读成<条数>

## 答案
```
SELECT
    customer_number
FROM
    orders
GROUP BY customer_number
ORDER BY COUNT(*) desc
LIMIT 1;
```
