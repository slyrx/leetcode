## 题目理解
+ 输出是水果的数量
+ 输入是树的种类数组，一次只能从一棵树摘一个水果
+ 本质是在记录，两种元素连接的最长距离

## 处理方式
+ 列举所有可能的情况
+ + 没有数据的情况
+ + 从头到尾都是符合的元素
+ + 后面出现其它元素，但是没有超过前面，在 max(sub_len, i-start+1) 中保留 sub_len。
+ + 后面出现其它元素，超过了前面的元素，在 max(sub_len, i-start+1) 中保留 sub_len。

## 关键
+ 在检查种类数量的时候，超出以后，对数量减1操作，决定了 start 指针的移动情况

## 答案
```
class Solution(object):
    def totalFruit(self, tree):
        """
        :type tree: List[int]
        :rtype: int
        """
        
        if len(tree) == 0:
            return 0
        
        start = 0
        board = {}
        sub_len = 0
        
        for i,x in enumerate(tree):
            if x not in board:
                board[x] = 1
            else:
                board[x] += 1
            
            if len(board) > 2:
                board[tree[start]] -= 1
                
                if board[tree[start]] == 0:
                    del board[tree[start]]
                    
                start += 1
                
            sub_len = max(sub_len, i-start+1)
            
        return sub_len
```
