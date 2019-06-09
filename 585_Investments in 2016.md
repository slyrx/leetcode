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

+ 原表链接浮动表格的关键是 where x **in** (浮动表格)

## SQL语句
+ group by 以某个属性来分组。
+ CONCAT() CONCAT(s1,s2...sn),字符串 s1,s2 等多个字符串合并为一个字符串

## 内置函数
+ count() 计数，count(*)括号中的*表示将所有筛选出的结果计数。
+ sum() 统计求和

## 语法
+ where count(*) >1 中的*表示什么？包括了所有的列，相当于行数，在统计结果的时候，不会忽略列值为NULL 
+ from insurance as tl 将表格名称重命名为t1之后，如果还使用原表名insurance，会报“Unknown column 'insurance.TIV_2015' in 'IN/ALL/ANY subquery'”错误。<br>
因此在后续的时候中，需要使用别名tl。

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

## 答案
select sum(ti.TIV_2016) as TIV_2016<br>
from insurance as ti<br>
where ti.TIV_2015 in (<br>
    select TIV_2015 <br>
    from insurance<br>
    group by TIV_2015<br>
    having count(*) > 1<br>
) and concat(LAT,LON) in (<br>
    select concat(LAT,LON)<br>
    from insurance<br>
    group by concat(LAT,LON)<br>
    having count(*) = 1<br>
)
