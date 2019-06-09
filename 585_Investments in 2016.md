## 单词
+ to a scale of 2 decimal places， 到2位小数的比例
+ policy 保险单
+ policyholders 保险客户;投保人
+ criteria 标准
+ latitude 纬度
+ longitude 经度
+ attribute pairs 属性对


## 浮动表
+ 同一列中相同值的筛选,需要选择浮动表的形式，要想使用浮动表格，就需要单独使用一套select语句。

SELECT TIV_2015<br>
FROM  insurance<br>
GROUP BY TIV_2015<br>
HAVING COUNT(*) > 1<br>

## SQL语句
+ group by 以某个属性来分组。

## 内置函数
+ count() 计数

## 语法
+ where count(*) >1 中的*表示什么？包括了所有的列，相当于行数，在统计结果的时候，不会忽略列值为NULL 

## SQL语句的执行顺序
(8)SELECT  (9) DISTINCT (11) <TOP_specification> <select_list><br>
(1)  FROM <left_table><br>
(3) <join_type> JOIN <right_table><br>
(2) ON <join_condition><br>
(4) WHERE <where_condition><br>
(5) GROUP BY <group_by_list><br>
(6) WITH {CUBE | ROLLUP}<br>
(7) HAVING <having_condition><br>
(10) ORDER BY <order_by_list>

+ group by 在where语句后才开始执行，因此在group by之后再增加筛选条件，需要使用关键词
