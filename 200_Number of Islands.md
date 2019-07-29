## 思路
+ 利用 DFS 实现，包括两个部分：
+ + DFS 函数本身
+ + 主函数调用 DFS

## 关键
+ 边界范围的确定
+ + 最大边界超过长度的部分为 i >**=** len(grid)
+ + 最小边界 i<0
+ + 以及内容不为1的元素

## 答案
```
class Solution(object):
    def numIslands(self, grid):
        """
        :type grid: List[List[str]]
        :rtype: int
        """
        def DFS(grid, i, j):
            if i<0 or j<0 or i>=len(grid) or j>=len(grid[0]) or grid[i][j] != "1":
                return
            
            grid[i][j] = "#"
            
            DFS(grid, i-1, j)
            DFS(grid, i+1, j)
            DFS(grid, i, j-1)
            DFS(grid, i, j+1)
            
        if len(grid) == 0:
            return 0
        
        r = len(grid)
        c = len(grid[0])
        count = 0
        
        for i in range(r):
            for j in range(c):
                if grid[i][j] == "1":
                    count += 1
                    DFS(grid, i, j)
                    
        return count
```
