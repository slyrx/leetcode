## 思路
1. 列出题目要求的规则
2. 先依次遍历每个元素
3. 统计每个元素周边的情况
4. 将统计情况经过筛选条件进行过滤、操作
5. 将结果转换为0和1表示

## 关键

## 涉及情况

## 答案
```
class Solution(object):
    def gameOfLife(self, board):
        """
        :type board: List[List[int]]
        :rtype: None Do not return anything, modify board in-place instead.
        """
        
        def count(board, i, j):
            iend, jend = len(board), len(board[0])
            count = 0
            
            if i-1>=0 and j-1>=0: count += board[i-1][j-1]%2
            if i-1>=0: count += board[i-1][j]%2
            if i-1>=0 and j+1<jend: count += board[i-1][j+1]%2
            if j-1>=0: count += board[i][j-1]%2
            if j+1<jend: count += board[i][j+1]%2
            if i+1<iend and j-1>=0: count += board[i+1][j-1]%2
            if i+1<iend: count += board[i+1][j]%2
            if i+1<iend and j+1<jend: count += board[i+1][j+1]%2
            
            return count
        
        for i in range(len(board)):
            for j in range(len(board[0])):
                if board[i][j] == 0:
                    if count(board, i, j) == 3:
                        board[i][j] = 2
                else:
                    if count(board, i, j) < 2 or count(board, i, j)>3:
                        board[i][j] = 3
                        
        for i in range(len(board)):
            for j in range(len(board[0])):
                if board[i][j] == 3:
                    board[i][j] = 0
                elif board[i][j] == 2:
                    board[i][j] = 1
                    
```
