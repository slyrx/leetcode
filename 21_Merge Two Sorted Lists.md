## 单词
+ splicing 衔接

## 关键点
+ 临时指针和返回指针可以先随便new一个节点，这样可以利用next指针。而赋值成None就没办法用了。
+ 有一个链表有剩余如何处理？
```
start.next = l1 if l1 else l2
```


## 问题
+ 返回点指针如何定义
+ mergeTwoLists如何return
+ 答案是使用迭代写的
+ 是不是能用递归实现呢？
