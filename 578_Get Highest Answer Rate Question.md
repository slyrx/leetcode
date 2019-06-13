
## 目的
+ 查找最高回答率的问题
+ + 每个answer_id的回答状态

## 思路
+ answer_id不为null的
+ 再对question_id进行分组

## 关键
+ 除了扩表操作，还有***缩表***操作。
+ + 缩表就是 把select的结果作为一个新表，再select

## 答案
```
select t2.question_id as survey_log
from (
select question_id, answer_id
from survey_log as t1
where answer_id is not null
) as t2
group by t2.question_id
order by count(*) desc
limit 1;
```
