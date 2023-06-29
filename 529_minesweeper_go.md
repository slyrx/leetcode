# 题目描述

# 解题思路
对于给定的坐标click，判断它是否是地雷，如果是则将其改为'X'并返回；
如果不是地雷，则统计其周围8个方块中地雷的数量count，并将当前方块的值设置为对应的数字；
如果count为0，表示当前方块周围没有地雷，可以继续递归挖掘周围的方块，将其设为'B'，并对周围的方块递归调用扫雷函数；
如果count不为0，表示当前方块周围有地雷，只需要更新当前方块的值为count即可。


# 实现代码
```golang

func updateBoard(board [][]byte, click []int) [][]byte {
    row, col := click[0], click[1]
    if board[row][col] == 'M' {
        // 点击的方块是地雷，游戏结束
        board[row][col] = 'X'
    } else {
        dfs(board, row, col)
    }
    return board
}

func dfs(board [][]byte, row, col int) {
    if row < 0 || row >= len(board) || col < 0 || col >= len(board[0]) || board[row][col] != 'E' {
        // 越界或当前方块不是未挖出的空方块，直接返回
        return
    }

    // 统计周围方块中地雷的数量
    count := 0
    directions := [][]int{{-1, -1}, {-1, 0}, {-1, 1}, {0, -1}, {0, 1}, {1, -1}, {1, 0}, {1, 1}}
    for _, dir := range directions {
        newRow, newCol := row+dir[0], col+dir[1]
        if newRow >= 0 && newRow < len(board) && newCol >= 0 && newCol < len(board[0]) && board[newRow][newCol] == 'M' {
            count++
        }
    }

    if count == 0 {
        // 周围没有地雷，递归挖掘周围的方块
        board[row][col] = 'B'
        for _, dir := range directions {
            newRow, newCol := row+dir[0], col+dir[1]
            dfs(board, newRow, newCol)
        }
    } else {
        // 周围有地雷，显示地雷数量
        board[row][col] = byte('0' + count)
    }
}

```

# 时间复杂度

# 空间复杂度
