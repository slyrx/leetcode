## 单词
+ referee 推荐人

## 目的
+ 查询客户推荐人不是2的名单

## 错误答案1
```
select name
from customer
where referee_id != 2;
```
+ 没有处理NULL的情况

## 错误答案2
```
SELECT name FROM customer WHERE referee_id = NULL OR referee_id <> 2;
```
+ sql里只有is null 和 is not null 的操作
+ 没有直接和null做等价运算的。

## 增加NULL的处理
+ OR referee_id is NULL

## 答案
```
select name
from customer
where referee_id <> 2 or referee_id is null;
```
