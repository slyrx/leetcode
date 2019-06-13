## 目的
+ 找出获胜的候选者

## 思路
+ 投票表中出现次数最多的CandidateId

## 不完整答案
```
select t3.Name
from (
select t1.CandidateId
from Vote as t1
group by t1.CandidateId
order by count(*) desc
) as t2
left join Candidate as t3
on t2.CandidateId = t3.id
```
+ 如何确保取的是最多投票数的？
+ 如果有两个或多个人都最多，怎么动态取得这个人数？
+ + 标准答案里没有这种考虑，只是取第一个

## 问题
+ 在子表中把顺序关系丢失了，因此后面的处理开始错乱。
+ 如果是空值如何处理？
+ + Candidate的信息为空，如何处理？
+ + 使用left join 和 inner join的区别
+ + 如果空的是主表，则返回结果是[]，如果空的是副表则返回结果是[null]
+ 获得投票最多的人不再Candidate表中。
+ + 因此需要先过滤出最高的那个人，在与Candidate表合并

## 答案

