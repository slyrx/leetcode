## 单词
byte 字节

bit 位

least significant 8 bits 最低有效8位

Only the least significant 8 bits of each integer is used to store the data. 只有最低8位有效位会被用于存储数据，也就是说当一个整数大到8位表示不下的时候，也只取它的低8位。

This means each integer represents only 1 byte of data. 

## 困难
逻辑清晰，使用什么样的实现方法不明确。光会道了，术不熟练。头脑中浮现出很多循环遍历的逻辑，感觉就错很多了。

## 思路
一遍循环，外加一个检验标记，就可以同时执行多段的检查。


## 关键
1. 知道 0b 的含义。
2. 8位向右移动5，4，3位，可以剩余标记头
3. 标记位的两个方面可以作为信号: 
+ 是否为0
+ 不为0时的数值大小
4. 每一位上做两个判断
+ 是不是开头标记，通过该位对应的 cnt 来判断
+ 是不是 10 标记，通过该位对应的 cnt 来判断，cnt 可以是多个，更节省内存的做法是用一个变量，实时更新，只记录当前的位置的 cnt 状态。



## 涉及的情况

## 答案
