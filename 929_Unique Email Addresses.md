## 单词
+ local name 本地名
+ domain name 域名
+ periods 句号


## 题意规则
+ . 在本地名中被忽略。
+ \+ 在本地名中其及后面的内容被忽略。
+ 返回独立的email地址列表。


## 处理流程
1. 遍历整个列表
2. 将email地址的本地名和域名分开
3. 检查本地名中是否有\+号，如果存在则截取从头位置到\+号索引前的内容
4. 检查剩余的内容是否有.号，如果有用""空替换掉。


## 错误
+ AttributeError: 'unicode' object has no attribute 'slice'<br>
字符串中没有slice函数，直接使用数组的切片操作。
+ 切片操作中[0， local_name.index("+")]，不能是，号，更不能呢是中文逗号，应该是英文冒号:
+ 返回值变量名写错了
+ 要求返回**独立**的邮件列表，没有增加唯一性处理。<br>
返回列表应该使用set，而不是数组，保证了唯一性。
+ AttributeError: 'set' object has no attribute 'append'，set没有append方法，有add，作用相同。
