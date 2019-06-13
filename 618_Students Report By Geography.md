## 单词
+ A U.S graduate school 美国研究生院
+ continent 大陆

## 目的
+ 转置
+ 查询含学生最多的

## 思路
+ SELECT @am:=0
+ + 设置变量，名称为@am，初始值为0，赋值符号:=, @表示声明变量
+ + 设置变量用的set语句就是select

#### 一个列的统计思路
```
SELECT 
    row_id, America
FROM
    (SELECT @am:=0) t,
    (SELECT 
        @am:=@am + 1 AS row_id, name AS America
    FROM
        student
    WHERE
        continent = 'America'
    ORDER BY America) AS t2
;
```

#### 多个列的统计思路
+ 使用join的逻辑，将独立找出来的列拼接成新表
```
SELECT 
    America, Asia, Europe
FROM
    (SELECT @as:=0, @am:=0, @eu:=0) t,
    (SELECT 
        @as:=@as + 1 AS asid, name AS Asia
    FROM
        student
    WHERE
        continent = 'Asia'
    ORDER BY Asia) AS t1
        RIGHT JOIN
    (SELECT 
        @am:=@am + 1 AS amid, name AS America
    FROM
        student
    WHERE
        continent = 'America'
    ORDER BY America) AS t2 ON asid = amid
        LEFT JOIN
    (SELECT 
        @eu:=@eu + 1 AS euid, name AS Europe
    FROM
        student
    WHERE
        continent = 'Europe'
    ORDER BY Europe) AS t3 ON amid = euid
;
```

## 答案
```
SELECT 
    America, Asia, Europe
FROM
    (SELECT @as:=0, @am:=0, @eu:=0) t,
    (SELECT 
        @as:=@as + 1 AS asid, name AS Asia
    FROM
        student
    WHERE
        continent = 'Asia'
    ORDER BY Asia) AS t1
        RIGHT JOIN
    (SELECT 
        @am:=@am + 1 AS amid, name AS America
    FROM
        student
    WHERE
        continent = 'America'
    ORDER BY America) AS t2 ON asid = amid
        LEFT JOIN
    (SELECT 
        @eu:=@eu + 1 AS euid, name AS Europe
    FROM
        student
    WHERE
        continent = 'Europe'
    ORDER BY Europe) AS t3 ON amid = euid
;
```
