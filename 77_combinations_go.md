# 题目描述
在 1～n 的数字里，找组成 k 的位的组合。

# 解题思路
回溯

有点儿没搞清楚，回溯是对谁回溯。
简单点儿理解，就是谁 append ，就对谁回溯。

对应的一维数组，需要被 append 和回溯，结果放在 combination 中。

# 实现代码
```golang

func combine(n int, k int) [][]int {
    var combinations [][]int // 存储组合结果的二维数组

    // 调用回溯函数，传入起始数字 1，整数 n，数字个数 k，空的路径数组和组合结果集的指针
    backtrack(1, n, k, []int{}, &combinations)

    return combinations // 返回组合结果
}

func backtrack(start, n, k int, path []int, combinations *[][]int) {
    // 如果路径数组的长度达到了 k，表示已经选择了 k 个数字，将当前路径加入结果集中
    if len(path) == k {
        temp := make([]int, k)
        copy(temp, path)
        *combinations = append(*combinations, temp)
        return
    }

    // 遍历从 start 到 n 的数字
    for i := start; i <= n; i++ {
        // 将当前数字加入路径数组中
        path = append(path, i)

        // 递归调用回溯函数，起始数字为当前数字的下一个数字，继续选择剩余的数字
        backtrack(i+1, n, k, path, combinations)

        // 在递归返回后，将路径数组的最后一个数字移除，以便进行下一次选择
        path = path[:len(path)-1]
    }
}

```

# 时间复杂度
O(k * C(n, k))
# 空间复杂度
O(k * C(n, k))
