## 题意
给一个大写字母的矩阵，给一个单词，求问该单词能在该矩阵中查找到吗？查找的顺序可以是横向和竖向的

## 输入
二维矩阵，和 字符数组

## 输出
布尔类型

## 答案代码
```
def exist(self, board, word):
        """
        :type board: List[List[str]]
        :type word: str
        :rtype: bool
        """
        
        def dfs(board, i, j, word, counts, visited):
            if counts == len(word):
                return True            
            if i<0 or i==len(board) or j<0 or j==len(board[0]) or visited.get((i,j)) or (word[counts] != board[i][j]):
                return False

            
            visited[(i,j)] = True
            res = dfs(board, i-1, j, word, counts+1, visited) or\
                  dfs(board, i+1, j, word, counts+1, visited) or\
                  dfs(board, i, j-1, word, counts+1, visited) or\
                  dfs(board, i, j+1, word, counts+1, visited)
            visited[(i,j)] = False
            
            return res
        
        visited = {}
        for i in xrange(len(board)):
            for j in xrange(len(board[0])):
                if dfs(board, i, j, word, 0, visited):
                    return True
                
                
        return False
```
