## 问题
+ 在统计只出现一次的问题时，使用
```
group by
having count(*) = 1
```
+ 如何在group by的结果中取最大值？
与答案的不同之处在于，将group by的结果作为表再查询一次。
+ 因为选择创建出来的表，必须配备表名
```
Every derived table must have its own alias
```

## 答案
```

SELECT
    MAX(num) AS num
FROM
    (SELECT
        num
    FROM
        my_numbers
    GROUP BY num
    HAVING COUNT(num) = 1) AS t
```
